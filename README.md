# CrealityK2Plus_sweep

Independent investigation of the phone-home behavior of the Creality K2 Plus 3D printer, framed neutrally as documented observable facts.

**Subject:** Creality K2 Plus, OpenWrt 21.02-snapshot + Klipper + Moonraker, Allwinner T113-S3 SoC. OTA firmware version V1.1.5.5 (release date 2026-05-08).

**Investigator:** Jay Puckett, Obsidian Watch Group, investigations@obsidianwatch.org. GPG fingerprint `9267A71E3F0A4EED2F973F9BA3E252F24635CC6C`.

**Status (2026-05-30):** Initial sweep complete.

## Why this exists

The K2 Plus's setup flow asks the user to consent to a Terms of Use clause that explicitly enumerates collection of **password, passphrase, user ID, account ID, network ID, and password again**. The investigator declined the ToU and wanted to document what the device actually does on the wire and in firmware regardless of the consent answer.

This repository documents observable facts. Where an observation has a benign explanation, that is noted. Where the investigator cannot determine intent or purpose, the report says so. Readers (consumers, regulators, security researchers) are left to draw conclusions appropriate to their own interest.

## Read

- **[FINAL_REPORT.md](FINAL_REPORT.md)** is the consolidated final paper. Observed facts, methodology, mitigations, and disclosure routes.
- [METHODOLOGY.md](METHODOLOGY.md), exact commands, tools, and capture topology.
- [CHAIN_OF_CUSTODY.md](CHAIN_OF_CUSTODY.md), how artifacts were acquired and handled.
- [ARTIFACTS.md](ARTIFACTS.md), index of pcaps, firmware images, hashes, extracted files.

## Reproducibility

Every observation in this repository is reproducible from an unmodified K2 Plus on the same firmware. The capture commands are in [METHODOLOGY.md](METHODOLOGY.md). The firmware download URL and SHA-256 are in [ARTIFACTS.md](ARTIFACTS.md). No exploits or vulnerabilities were used. Every observation came from watching the device's normal traffic or analyzing its publicly downloadable OTA image. The default root password is publicly documented.

## Disclosure

Findings are being prepared for delivery to FTC consumer protection, Mozilla *Privacy Not Included*, and CISA. See [FINAL_REPORT.md §4](FINAL_REPORT.md) for the disclosure plan.
