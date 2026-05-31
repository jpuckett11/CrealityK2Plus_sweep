# Chain of Custody

All artifacts referenced in the reports were acquired and handled as follows. The intent is that an independent investigator could reproduce the same findings from the same sources without trusting any intermediate file.

## Unit identification

| Field | Value |
|---|---|
| Model | Creality K2 Plus |
| Hostname (Moonraker) | `K2Plus-XXXX` |
| WiFi MAC (initial, since discarded) | `fc:ee:28:XX:XX:XX` |
| Wired MAC | `8e:XX:XX:XX:XX:XX` (locally-administered / randomized) |
| Acquisition | Retail purchase by investigator, used on shipped firmware |
| OEM-reported model code (from OTA naming) | `CR0CN240110C10` |
| SoC | Allwinner T113-S3 (dual ARMv7 Cortex-A7, 500 MB RAM) |
| Operating distribution | OpenWrt 21.02-SNAPSHOT |
| Investigation period | 2026-05-30, ongoing 48-hour capture through 2026-06-01 |

## Network capture artifacts

| Path | Description | SHA-256 | Bytes |
|---|---|---|---|
| `~/captures/k2plus_passive_20260530-145844.pcap` | Pre-MITM passive broadcast capture (~14 min). Confirms mDNS announcements from the device. | (computed at archive time, see ARTIFACTS.md) | 36 KB |
| `~/captures/k2plus_pre-reboot_154325.pcap` | First MITM capture window; ~5 minutes. Contains the first TLS SNI to `api.crealitycloud.com`, the OTA firmware push (162 MB downstream in 42 s), and the initial NTP exchange with `time.neu.edu.cn`. | (computed at archive time) | 164 MB |
| `~/captures/48hr_monitor/k2plus_*.pcap` | Rotating 48-hour MITM capture. Hourly rollover, 100 MB cap per file, 60-file retention. | (per-file at archive time) | rolling |

Capture commands and topology are documented in [METHODOLOGY.md](METHODOLOGY.md).

## Firmware artifact

| Field | Value |
|---|---|
| Filename | `CR0CN240110C10_R_202605081127_ota_img_V1.1.5.5.img` |
| Vendor URL | `https://file2-cdn.creality.com/file/061e5074c360584d65ff4ae3aba9c028/CR0CN240110C10_R_202605081127_ota_img_V1.1.5.5.img` |
| Acquired (UTC) | 2026-05-30 22:18 |
| Acquired via | unauthenticated `curl` from URL discovered by scraping `https://www.crealitycloud.com/downloads/firmware/flagship-series/k2-plus` |
| Bytes | 142,381,568 |
| SHA-256 | `d83e738cca980202391fc60ad039f850368e98a0836679111145e6e28ae1698d` |
| Underlying storage | Alibaba Cloud OSS (per `x-oss-*` headers, 136-part multipart upload), Cloudflare-fronted |
| Format | SWUpdate cpio archive (`ASCII cpio archive (SVR4 with CRC)`) containing `sw-description`, `uboot`, `kernel`, `rootfs` |
| `rootfs` format | Squashfs v4.0, zlib compressed, 11,853 inodes, created 2025-12-11 03:08:47 UTC |
| Local path | `~/k2plus_firmware/CR0CN240110C10_V1.1.5.5.img` (excluded from git via `.gitignore`) |
| Extraction target | `~/k2plus_firmware/extracted/` |

The firmware was downloaded by the investigator's workstation directly from Cloudflare's CDN, the printer itself was not contacted to obtain it. The download is therefore independent of any device-specific state and is exactly the same bytes any K2 Plus would pull during its next OTA cycle.

## Identity material from extracted rootfs

| Path in rootfs | Description | Disposition |
|---|---|---|
| `etc/shadow` | Contains root password hash `$5$d5o85tQWWFj2/jfn$hbfxMqPeiEXFAn9vLPDw/8KFTnC2I3GN1uQ2mQAh7r1` (SHA-256-crypt) | Saved separately at `~/k2plus_firmware/crack/hash_only.txt` for offline cracking; not committed to this repo. |
| `usr/share/cert/server.crt` | Embedded server cert. `CN=My Server, O=Internal Service, C=CN`. Self-signed by the embedded CA below. | Cited in report 04 |
| `usr/share/cert/ca.crt` | Embedded CA cert. `CN=My Private CA, O=Internal Network, C=CN`. Valid 2025-08-28 → 2035-08-26. | Cited in report 04 |
| `usr/share/cert/server.key` | Plaintext private key for `server.crt`. **Shipped in the OTA, available to anyone who downloads the firmware.** | Cited in report 04. Not committed; original lives only in the local rootfs extraction. |

## Disclosure handling

Captures and firmware are retained on the investigator's workstation only. No artifacts have been shared with third parties as of the date of this commit. Hashes above are sufficient for any future recipient to verify they have the same bytes the investigator analyzed.

When this material is shipped to a regulator or recipient, the recipient's identifier and date will be appended to this file.
