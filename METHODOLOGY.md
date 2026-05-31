# Methodology

All work performed 2026-05-30 on the investigator's home LAN (`<LAN-SUBNET>`) from an Ubuntu 24.04 workstation. The K2 Plus was a retail-purchased unit operating on its shipped firmware, connected first to WiFi for fingerprinting, then to wired ethernet for the bulk of the capture.

## 1. Discovery and fingerprinting

- `nmap -sn -PR -n <LAN-SUBNET>` for L2 ARP enumeration of the LAN.
- `nmap -Pn -p- --min-rate 2000 -T4 <PRINTER-LAN>` (the printer's first IP), discovered open ports 22 (Dropbear SSH), 80 (httpd), 4408, 5037 (ADB), 7125 (Moonraker), 8000 (WebRTC video), 9999.
- `curl http://<PRINTER-LAN>:7125/printer/info` and `…/machine/system_info`, Moonraker is unauthenticated for any RFC1918 client by default (`force_logins: false`, `trusted_clients` includes all private ranges). Returned hostname `K2Plus-XXXX`, Klipper version, distribution `OpenWrt 21.02-SNAPSHOT`, interface MACs.

## 2. Network capture

### 2.1 Topology problem

The investigator's workstation was originally on a different subnet (`192.168.2.0/24`) than the printer, with two routing hops between them. WiFi association of the workstation to the printer's SSID was required before any direct L2 visibility was possible. Even once on the same SSID, WiFi's per-station pairwise encryption means a passive `tcpdump` from one station cannot read unicast frames sent by another station.

To see the printer's outbound unicast traffic, an active ARP MITM was required.

### 2.2 ARP MITM

After the user switched the printer from WiFi to wired ethernet (printer received `<PRINTER-LAN>` on its wired interface, MAC `8E:XX:XX:XX:XX:XX`), ettercap was used to poison both the printer's and the gateway's ARP tables:

```
sudo ettercap -T -q -i wlp11s0 -M arp:remote \
  8e:XX:XX:XX:XX:XX/<PRINTER-LAN>// \
  90:93:5a:XX:XX:XX/<GATEWAY-LAN>//
```

IP forwarding was already enabled (`net.ipv4.ip_forward=1`) so the workstation transparently relayed packets between printer and gateway.

### 2.3 Capture

```
sudo tcpdump -i wlp11s0 -n -s 0 -U -Z obsidian \
  -G 3600 -W 60 -C 100 \
  -w /home/obsidian/captures/48hr_monitor/k2plus_%Y%m%d-%H%M%S.pcap \
  'host <PRINTER-LAN> or ether host 8e:XX:XX:XX:XX:XX
   or (udp port 67 or udp port 68)
   or (udp port 53 and (host <PRINTER-LAN> or host <GATEWAY-LAN>))'
```

`-G 3600 -W 60 -C 100` rotates files hourly, capped at 100 MB each, keeping the most recent 60 files (~60 hours of buffer). A supervisor script (`~/captures/48hr_monitor/supervisor.sh`) restarts `tcpdump` and `ettercap` if either dies and produces hourly snapshot analyses to `~/captures/48hr_monitor/snapshots/`.

### 2.4 What this captures and what it doesn't

The capture sees all L3 traffic between the printer and the internet, including TLS handshakes (so TLS SNI hostnames are visible). It does **not** decrypt TLS payloads, bodies of HTTPS requests are not readable. Cleartext protocols (MQTT on port 1883, NTP on 123, HTTP on 80) are fully readable.

## 3. Firmware analysis

The K2 Plus's OTA firmware is available without authentication from a Cloudflare-fronted URL discovered by scraping the JSON state on Creality's firmware download page:

```
curl -o CR0CN240110C10_V1.1.5.5.img \
  "https://file2-cdn.creality.com/file/061e5074c360584d65ff4ae3aba9c028/CR0CN240110C10_R_202605081127_ota_img_V1.1.5.5.img"
```

`HEAD` of that URL revealed the underlying storage is Alibaba Cloud OSS (`x-oss-*` headers, `x-oss-object-type: Multipart`, multipart-uploaded in 136 parts) with Cloudflare as the cache layer.

### 3.1 Extraction

The image is an `ASCII cpio archive (SVR4 with CRC)`, SWUpdate format, containing four entries:

```
sw-description       (manifest)
uboot                (Allwinner U-Boot)
kernel               (Android bootimg format)
rootfs               (Squashfs v4, gzip, 11853 inodes, 130MB compressed)
```

```
cpio -idmuv < CR0CN240110C10_V1.1.5.5.img
unsquashfs -d rootfs_extracted rootfs
```

### 3.2 Static analysis

- `strings` against the daemons (`master-server`, `wifi-server`, `app-server`, `display-server`, `upgrade-server`, `web-server`, `Monitor`, and the Go-based telemetry uploader `log_main`).
- Grep across the extracted rootfs for the URLs and IPs observed live.
- `openssl x509 -in usr/share/cert/server.crt -noout -subject -issuer` for the embedded cert pair.

## 4. Hash crack (in progress)

The root password hash from `etc/shadow` is SHA-256-crypt format (`$5$`). Cracking is offline against the extracted hash, no impact on the live device:

```
hashcat -m 7400 -a 3 hash_only.txt -1 '?l?d' '?1?1?1?1?1?1?1?1' \
  --increment --increment-min=4 --increment-max=8
```

Mask attack runs against the workstation's RTX 4090 (CUDA Toolkit not installed, falls back to OpenCL ≈ 30-80 kH/s for this algorithm). A targeted vendor-pattern wordlist was tried first and exhausted without a match.

## 5. What this investigation did not do

- **No tampering with the printer.** No SSH attempts succeeded; no files on the printer were modified; no firmware was flashed.
- **No exploitation.** Every observation is either (a) a passive read of public OTA artifacts, or (b) an active ARP MITM on the investigator's own LAN (legal on a network you own; consent assumed).
- **No TLS decryption.** Without a forged CA cert in the printer's trust store and a transparent proxy, HTTPS bodies are not visible. We see destinations, SNI hostnames, packet timing, and packet sizes only.
- **No physical disassembly.** The printer's hardware has not been opened. Hardware-component identification was not performed.
