# Artifacts Index

Per-artifact hashes and provenance. Large binary artifacts (pcaps, firmware images, extracted filesystems) are excluded from the repository via `.gitignore`; their hashes appear here so independent recipients can verify their copies.

## Firmware

| Filename | Bytes | SHA-256 | Source |
|---|---|---|---|
| `CR0CN240110C10_R_202605081127_ota_img_V1.1.5.5.img` | 142,381,568 | `d83e738cca980202391fc60ad039f850368e98a0836679111145e6e28ae1698d` | `https://file2-cdn.creality.com/file/061e5074c360584d65ff4ae3aba9c028/CR0CN240110C10_R_202605081127_ota_img_V1.1.5.5.img` |

Underlying storage: Alibaba Cloud Object Storage (`x-oss-*` headers, multipart 136-part). Last-Modified per the OSS object: 2026-05-14 01:34:26 UTC. CDN-fronted by Cloudflare.

## Other K2-family firmware URLs harvested from the same vendor page

Recorded for completeness and cross-referencing; not yet downloaded or analyzed.

```
# K2 Plus main system (CR0CN240110C10):
V1.1.0.57, V1.1.0.65, V1.1.1.5, V1.1.1.7, V1.1.2.6, V1.1.2.10,
V1.1.3.13, V1.1.4.8, V1.1.4.11 (officially "latest released"),
V1.1.5.2, V1.1.5.5 (latest in CDN, downloaded)

# K2 Plus CFS / accessory (CR0CN200400C10):
V1.1.0.53, V1.1.0.66, V1.1.0.94, V1.1.3.6, V1.1.3.8, V1.1.4.1, V1.1.5.5

# Other models cataloged on the same page:
CR4CU220812S11 (K2 SE), CR4CU220812S12 (X2000E), CR4SU200382C13 (K1C-2025)
```

URL pattern: `https://file2-cdn.creality.com/file/<32-char-hash>/<filename>.img`. Each URL is unauthenticated.

## Network captures

| Filename | Window | Bytes | Notes |
|---|---|---|---|
| `k2plus_passive_20260530-145844.pcap` | ~14 min, passive (no MITM) | 36 KB | mDNS, ARP, broadcasts only. Confirms the printer's `_Creality-XXXXXXXXXXXX._udp.local` service announcement and the placeholder `SN=SN_XXX.MAC=MAC_XXX` TXT record. |
| `k2plus_pre-reboot_154325.pcap` | ~5 min, MITM active | 164 MB | First evidence of `api.crealitycloud.com` TLS, OTA firmware push (162 MB downstream in 42 s), `time.neu.edu.cn` NTP. |
| `k2plus_reboot_20260530-154327.pcap` | Started ~17:43, intended to capture a power-cycle | rolling | Additional TLS SNIs `devdata.cxswyjy.com`, `api.ipify.org`, `pic2-cdn.creality.com`. Cleartext MQTT keepalive to `47.253.214.226:1883` (Alibaba Cloud LLC) captured. |
| `48hr_monitor/k2plus_*.pcap` | Rolling 48 hrs, hourly rotation, 100 MB cap each, 60 retained | rolling | Long-window capture intended to catch interval-driven beacons and OTA polling cycles. |

SHA-256 of each pcap is recorded by the supervisor at close-of-rotation and stored alongside the file. Authoritative hashes will be appended here when the 48-hour window closes.

## Extracted rootfs contents of interest

Hashes from the V1.1.5.5 rootfs (`d83e738c…`):

| Path in rootfs | SHA-256 (file content) | Bytes | Notes |
|---|---|---|---|
| `etc/shadow` | (computed locally) | | Root password hash, format `$5$` (SHA-256-crypt) |
| `etc/appetc/alchemistp/config.json` | (computed locally) | 1,504 | Cloud-endpoint configuration; the literal source of truth for hostnames the daemon talks to |
| `usr/lib/libcrealitycloud.so` | (computed locally) | | Cloud SDK; contains 16 API endpoints and the full domain inventory |
| `usr/lib/libalibabacloud-oss-cpp-sdk.so` | (computed locally) | | Alibaba Cloud Object Storage SDK (C++) |
| `usr/lib/liboss_c_sdk.so.3.0.0` | (computed locally) | | Alibaba Cloud Object Storage SDK (C) |
| `usr/bin/log_main` | (computed locally) | | Go-based telemetry uploader. Contains `dev_agent` package symbols including `AgreePrivacyStatus`. |
| `usr/bin/master-server` | (computed locally) | 1,912,752 | Master daemon coordinator |
| `usr/bin/wifi-server` | (computed locally) | 124,272 | WiFi credential / config handler |
| `usr/bin/app-server` | (computed locally) | 591,968 | Application logic; references `qr.creality.com/scan-code?n=` |
| `usr/bin/display-server` | (computed locally) | 19,281,980 | LCD UI (large because it bundles assets) |
| `usr/bin/upgrade-server` | (computed locally) | 120,176 | OTA decision logic |
| `usr/bin/web-server` | (computed locally) | 1,144,364 | HTTPD for ports 80/4408/etc |
| `usr/bin/Monitor` | (computed locally) | 42,984 | Process monitor |
| `usr/bin/get_sn_mac.sh` | (computed locally) | | Script that pulls SN / MAC / model / board / pcba_test / machine_sn / structure_version / stress_test via `/usr/bin/keybox` |
| `etc/init.d/app` | (computed locally) | | Init script that starts the 8 application servers above |

Authoritative hashes of these files will be appended to this index when the rootfs is re-extracted into the immutable archive (see [CHAIN_OF_CUSTODY.md](CHAIN_OF_CUSTODY.md)).

## Working files (not committed)

- `~/captures/48hr_monitor/snapshots/`, hourly analysis snapshots (TLS SNI list, DNS query list, unique destinations)
- `~/captures/48hr_monitor/alerts.log`, appends whenever a previously-unseen SNI or external destination appears
- `~/k2plus_firmware/crack/`, hashcat state, wordlists, and any cracked output

When the 48-hour window closes and the analysis is finalized, the snapshots and alerts log will be promoted into `scratch/` in this repo and (where relevant) into specific reports.
