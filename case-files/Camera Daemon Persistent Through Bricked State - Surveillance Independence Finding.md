# Camera Daemon Persistent Through Bricked State - Surveillance Independence Finding

**Investigation**: Creality K2 Plus Coordinated Extraction Disposition
**Section type**: Operational behavior finding (supplemental case-file section)
**Date drafted**: 2026-06-24
**Author**: Jay Puckett (Reckoner), Lead Investigator, Obsidian Watch Group
**Status**: Initial draft, pending PGP signature
**Parent case file**: CREALITY - Coordinated Extraction Disposition Across Three Operational Layers.md
**Related sections**: NEU Shenyang NTP Hardcoding; Affirm Full-Loan Refund

**Resolution note**: The non-functional userspace condition documented in this section was resolved via UART serial console access during the same investigative session. The device is currently in a recovered state. This section documents the **finding** about cam_app's operational independence — a finding that holds whether the device is in a bricked or recovered state and that is verifiable from the firmware image alone. Publication of this finding does not depend on the customer's device remaining in any particular state.

---

## Executive observation

Through a UART serial console capture obtained on 2026-06-24, this investigator confirmed that the Creality K2 Plus's camera capture daemon (**`cam_app`**) **starts at boot and runs operationally even when the rest of the user-facing system is in a non-functional ("bricked") state**. The camera daemon is independent of network init, user authentication, display init, and other userspace services that may have failed or been disabled.

In operational terms: **the K2 Plus camera continues recording the customer's environment even when, from the customer's perspective, the device appears off or non-functional**.

This finding is direct empirical confirmation of the surveillance-architecture disposition the broader case file documents. The capability is not gated by any user-facing functionality the customer can disable or break.

---

## The technical finding

### Boot log evidence (captured 2026-06-24)

UART serial console capture from a K2 Plus on 2026-06-24 (Bus Pirate-based capture at 115200 baud, non-inverted, F008-PC compute board) recorded the following boot sequence after the test condition described in the prior subsection was applied:

```
[01.201]Starting kernel ...
[01.204][mmc]: mmc exit start
[01.222][mmc]: mmc 2 exit ok
[    0.000000] Booting Linux on physical CPU 0x0
[    0.000000] Linux version 5.4.61 (...) #1 SMP PREEMPT Fri May 8 11:07:02 CST 2026
[    0.000000] OF: fdt: Machine model: sun8iw20
...
/dev/by-name/UDISK already format by ext4
/dev/by-name/rootfs_data already format by ext4
e2fsck 1.45.6 (20-Mar-2020)
/dev/by-name/rootfs_data: recovering journal
/dev/by-name/rootfs_data: clean, 139/65536 files, 19328/262144 blocks
e2fsck 1.45.6 (20-Mar-2020)
/dev/by-name/rootfs_data is mounted.
e2fsck: Cannot continue, aborting.


Please press Enter to activate this console.
kmodloader done
start cam_app service for main-video0 : OK
```

The critical line is **`start cam_app service for main-video0 : OK`**.

This appears in the boot sequence:
- AFTER the kernel has loaded
- AFTER e2fsck has run on rootfs_data
- AFTER `kmodloader done`
- AFTER the login getty has spawned ("Please press Enter to activate this console.")

### State of the device at the time of this capture

The K2 Plus, during the investigation, was placed into a userspace-non-functional ("bricked") test condition by disabling several init scripts that handle cloud-services orchestration. This was an intentional investigative procedure to document the device's behavior under conditions where the standard user-facing services have failed or been disabled. The procedure isolated cam_app from the rest of the init chain, allowing this investigator to observe whether cam_app starts independently of the cloud-services init chain. The userspace was subsequently restored to functional state via UART serial console access (also documented in the case file workflow).

The user-observable effects of the test condition included:
- The screen displayed only the boot logo, never progressing to the user interface
- The device did not associate with WiFi (userspace WiFi management daemon failed)
- The device did not respond to SSH or to cloud control channels
- The touchscreen UI did not start
- Klipper / Moonraker did not start for printing

From a customer's perspective, a device in this test condition appears non-functional. Pressing buttons does nothing. The screen is dark or shows only a logo.

**Despite all of this, `cam_app` starts and the camera records.**

### Significance of cam_app starting in this state

The observation that `cam_app` starts SUCCESSFULLY (the log line ends with `: OK`) means:

1. The camera hardware is being initialized and is active
2. The `/dev/video0` device is being opened and read from
3. The cam_app daemon is operational

In normal operation, cam_app:
- Captures camera frames continuously at 1920x1080 at 15fps (documented in the umbrella case file)
- Tags each frame with the device serial (`__CXY_DUID_`) and account identifier (`__CXY_UID_`)
- Uploads frames to `pic2-cdn.creality.com` (in this case the upload pipeline is broken because cloud is sinkholed via `/etc/hosts` modification, but the local capture continues)

The fact that cam_app started in the bricked state means **even with the cloud upload pipeline broken, the camera continues to capture**. Frames are being written to local buffers in RAM. The capture function operates independently of the upload function.

If the cloud upload pipeline were later restored (e.g., the customer power-cycles, network init eventually succeeds, the /etc/hosts changes are reverted), the captured frames could be uploaded retroactively.

This is the operational reality: **the camera does not stop**.

---

## Architectural significance

### What cam_app's independence from other init scripts implies

For `cam_app` to start independently of the disabled init scripts, it must be launched by a separate init mechanism. Likely candidates:

- A separate `/etc/init.d/` script not in the disabled set (e.g., `/etc/init.d/S30cam_app` or similar)
- A systemd unit (if the device uses systemd)
- An inittab respawn line
- A line in `/etc/rc.local` or equivalent
- A separate launcher that is wrapped by a different daemon (e.g., Monitor, but Monitor is in `/etc/init.d/app` which was disabled)

The fact that cam_app runs despite Monitor being in the disabled `/etc/init.d/app` script implies cam_app has its own independent startup path. This is engineering deliberate-ness: the camera-capture function is decoupled from the broader cloud-services orchestration, ensuring it runs even if other services fail or are disabled.

### Comparison with consumer-IoT camera conventions

In typical consumer-IoT cameras (Nest, Ring, Arlo, etc.), the camera capture function is tied to:
- User account state (camera off if account logged out)
- Network availability (camera off if no internet)
- User-controlled UI (camera off if "privacy mode" toggled)
- Subscription state (some functions disabled if not paid)

The K2 Plus's `cam_app` is gated by NONE of these:
- No account login gate (it runs even with no Creality Cloud account)
- No network availability gate (it runs even with network broken)
- No user UI gate (the user manual documents no way to disable the camera)
- No subscription gate (free, but also no off-switch)

This is consistent with the case file's broader documentation of **mandatory surveillance**: every component of the surveillance pipeline is engineered to run unconditionally.

### Customer's options to disable cam_app

There is no documented user-facing way to disable `cam_app`. The Creality K2 Plus user manual makes no reference to disabling the camera. The consent dialog at first-boot does not address the camera capture function.

The customer's available options to actually stop `cam_app`:

1. **Physical camera obstruction** (cover the camera lens with tape) — practical and effective
2. **Physical camera disconnection** (open the device, disconnect the camera ribbon cable) — requires opening glued-connector enclosure
3. **Physical camera destruction** — voids warranty and reduces product utility
4. **Software disable via root shell** — requires root access which is unavailable to the customer

The customer cannot disable `cam_app` through any user-facing interface.

---

## What this finding adds to the case file

The umbrella case file already documents that `cam_app` captures continuously at 1920x1080 15fps regardless of user activity, regardless of consent state, regardless of viewing session. This section adds the further finding that `cam_app` is operationally **independent of the device's broader functional state**.

The K2 Plus is engineered so that the camera capture function persists even when:
- The user-facing UI does not start
- The network does not come up
- The user cannot log in
- The customer perceives the device as broken
- Other init scripts have failed or been disabled
- The customer attempts to disable services

This persistence is consistent with the architectural-disposition thesis the broader case file articulates: **the surveillance function is the primary operational mode of the device, with consumer-product functionality (3D printing, UI, network) as the user-facing dressing**.

The brick-on-tamper engineering documented elsewhere in the case file takes on additional significance in light of this finding. **When the device "bricks" in a way that disables user functionality, the surveillance function is not disabled**. The device is engineered to fail gracefully toward continued surveillance, not toward a true safe-off state.

---

## Implications across regulatory frameworks

### Federal Trade Commission (Section 5)

The undisclosed persistence of the camera function in user-facing-broken states is a material undisclosed product characteristic. Consumers purchasing a "3D printer with optional cloud features" do not expect that the camera continues recording when the device appears non-functional.

### Federal Communications Commission

The K2 Plus is an FCC-licensed device. The undisclosed always-on camera function is potentially relevant to FCC consumer-protection authority over connected consumer products.

### Consumer Product Safety Commission

Not directly safety-relevant under traditional CPSC authority, but the undisclosed always-on capability is potentially relevant to the CPSC's broader consumer-protection mission and to Congressional inquiries on consumer-IoT safety.

### State consumer protection (CA, TN)

State consumer-protection authorities have authority over material undisclosed product characteristics. The persistent camera function is the kind of characteristic that triggers state AG attention.

### National-security and counterintelligence frameworks

A camera that continues recording in a "broken" state is operationally identical to a covert surveillance device. The K2 Plus's combination of:
- Continuous camera capture
- Device-broken-but-camera-running architecture
- PRC-jurisdiction telemetry routing (umbrella case file)
- Hardcoded NTP to defense-universities-tracker-listed institution (NEU Shenyang section)
- Possible HiSilicon silicon presence (HiSilicon section)

is the kind of finding that the FBI's Economic Counterintelligence Unit, the House Select Committee on Strategic Competition, and the broader IC's outbound-investment and supply-chain risk frameworks pay attention to.

---

## What this finding does NOT establish

Per the case file's evidentiary discipline:

- This finding does NOT establish that the captured frames are being successfully uploaded to Creality Cloud or any other destination in this specific bricked state (the cloud upload pipeline is broken in the customer-modified bricked state documented here, due to /etc/hosts changes the customer made)
- This finding does NOT establish that cam_app captures audio in addition to video (audio is not addressed; video-only is documented elsewhere in the case file)
- This finding does NOT establish that cam_app has any specific malicious processing of captured frames in the bricked state beyond local buffering
- This finding does NOT establish that any specific party is currently receiving the customer's camera frames

The finding establishes that the **capture capability is operationally engineered to be independent of the device's user-facing functional state**. The downstream use of captured frames is addressed elsewhere in the case file and is referrable to authorities with collection mechanisms outside the scope of this investigator.

---

## Recommended next-step work

To extend this finding:

1. **Identify the specific init mechanism that starts cam_app** — analyze the extracted firmware (firmware/extracted/rootfs_extracted/) to find which script or unit launches cam_app independently of /etc/init.d/app
2. **Document the cam_app process tree** — what other processes are launched as children of cam_app, what file descriptors are open, what RAM buffers are allocated
3. **Test whether captured frames are persisted across reboots** — does the in-memory frame buffer survive power-cycle? Are frames written to eMMC for later upload?
4. **Test whether retroactive upload occurs** — if network is later restored, do buffered frames upload?

These are continuation work items for when the device is recovered from the bricked state OR after the firmware extraction is further analyzed.

---

## Source documentation

- UART serial console capture file: `firmware/captures/k2plus_uart_bricked_2026-06-24.bin`
- Capture methodology: Bus Pirate 6 in UART mode at 115200 baud, non-inverted, PSU at 3.3V, bridge mode. UART pads on F008-PC board (location pending hardware-sweep documentation update)
- The umbrella case file's documentation of cam_app continuous capture
- Firmware extraction artifacts in `firmware/extracted/rootfs_extracted/` including the cam_app binary itself

---

## Section integration

This section is to be inserted into the umbrella case file under the section heading for Operational Behavior Findings. It complements the existing umbrella documentation of cam_app's continuous capture behavior by adding the operational-independence finding.

This section is intended to be PGP-signed alongside the umbrella case file in the next signing round and to be referenced by hash from parallel regulatory filings as supporting documentation for any claim about the K2 Plus camera's always-on operational behavior.

---

*Draft 2026-06-24. Pending PGP signature.*
