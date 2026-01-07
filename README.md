# HandsomeTello — The open micro drone

HandsomeTello turns the DJI Tello into an open, hackable micro drone: run lightweight Linux userspace, attach research payloads, and prototype autonomous behaviors for photogrammetry, environmental sensing, and robotics research.

## Quick highlights
- Target hardware: Tello / UZ801-derived WiFi SoC modding
- Goals: Linux userspace support, modular payloads, photogrammetry-ready toolchain
- Keywords: OpenStick, UZ801, Tello, photogrammetry, modular-drone, embedded-linux, microdrone

## Why the Ryze Tello was chosen
We selected the Ryze Tello as the baseline platform for HandsomeTello for practical and strategic reasons:
- Cheap, mass-produced, and accessible micro drone — widely available and low cost makes iterative experimentation and larger-scale testing feasible.
- API is open and documented — existing command/telemetry interfaces simplify integration, automation, and community contributions.
- Existing research and community projects — there is prior work to build upon or integrate with, accelerating development and reproducibility.
- Classified as a toy drone in many contexts — this typically results in fewer regulatory burdens in some jurisdictions (for example, no drone ID requirements where toy classification applies). Note: regulations and classifications vary by country and can change; always verify the current rules that apply to your location (see Responsible Use below).

## Attribution / Acknowledgements
This project builds on community hardware and software work. In particular:

- Handsome mod for the UZ801
  - Link: https://github.com/HandsomeMod
  - Attribution: Handsome UZ801 mod — hardware guidance and modifications used for UZ801-based expansion.

- Vim Vanthoog / OpenStick (OpenStick UZ801 v3.0 bundle)
  - Link: https://wvthoog.nl/openstick/
  - Attribution: OpenStick UZ801 resources and images used per upstream documentation.

Please ensure you respect the original authors' licenses and attributions. See CREDITS.md for details and links.

## About "microvandalism"
The term "microvandalism" appears in an associated white paper that documents research and scenarios explored during development. This repository documents technical work and research into small-form payloads, deployment mechanisms, and mitigation strategies; it does not endorse illegal activity. See the Responsible Use section below for important guidance.

## Deferred / Not-Included Features (time & financial constraints)
The list below describes features that were scoped and researched for HandsomeTello but were not implemented in the initial project release due to limited time and/or funding. They are documented here both to be transparent about project scope and to help potential contributors pick priority tasks.

- vGPS / NAVSOP / Assisted Navigation (cell-tower & Wi‑Fi)
  - What: Hybrid location/navigation using visual odometry (vGPS), NAVSOP-like sensor fusion, and cellular/Wi‑Fi assisted fixes to improve localization in GNSS-poor environments.
  - Reason deferred: Requires additional sensor integration, datasets for tuning, and substantial algorithm development and testing resources.

- Arduino Pro Mini via UART for low-power management, solar recharge, and autonomous return-to-home
  - What: Use a small MCU (Arduino Pro Mini) on UART for deep-sleep control, energy-budgeted solar recharge management, and an independent RTH (return-to-home) fail-safe when radio control is lost.
  - Reason deferred: Extra hardware, PCBs, and test rigs required for reliable power-management; also introduces hardware safety/regulatory testing overhead.

- Real-time low-bandwidth video transcoding (cell-network cost reduction)
  - What: On-board lightweight transcoder to reduce uplink bitrate for cellular streaming (codec/bitrate adaptation, frame-dropping, metadata-only modes).
  - Reason deferred: Requires optimized encoder toolchain for UZ801, real-time performance tuning, and cellular data usage testing (incurs recurring costs).

- openipc and/or wifi-broadcast-ng implementation
  - What: Replace or augment stock IPC (camera/stream) with openipc or experimental broadcast modes to enable local multicast, low-latency viewing, or opportunistic data-sharing.
  - Reason deferred: Complex reverse-engineering and compatibility testing; carries risk of destabilizing stock services unless isolated.

- USB‑OTG with the UZ801 as USB host (modular USB add-ons: SDR, LiDAR, sensors)
  - What: Enable UZ801 to act as USB host via OTG so users can attach low-cost USB sensors (SDR dongles, LiDAR, cameras, environmental sensors).
  - Reason deferred: Hardware wiring, power budgeting, and driver support (and likely ROM changes) require time and multiple hardware prototypes.

- Rooting / reverse engineering stock Tello firmware to enable hardware swaps (wi‑fi chip replacement, native USB OTG, USB video)
  - What: Deep firmware work to unlock or replace Wi‑Fi chipset support, enable native USB host/device functionality, or route video over USB.
  - Reason deferred: Highly time-consuming, legally and ethically sensitive in some jurisdictions, and may brick devices if done incorrectly. Requires careful responsible-disclosure practices.

- MAV / Micro Air Vehicle protocol integration and bridges
  - What: Bridge Tello control into MAV (MAVLink / micro air vehicle) ecosystems so it can be integrated with autopilots, GCSs, and simulators.
  - Reason deferred: Requires protocol-bridging middleware and test harnesses; Tello already exposes a simple UDP command interface, so a bridge is feasible but needs time to validate safe behaviors.

- Low-level Wi‑Fi chip security remediation / hardening
  - What: Fix or mitigate known Wi‑Fi chipset vulnerabilities, apply firmware patches, or add network isolation/firewalling.
  - Reason deferred: Patching firmware and verifying fixes can be costly and requires coordination with upstream maintainers and security researchers.

If you want a prioritized roadmap, we can produce one (short/medium/long term) and an estimation of hardware/software cost per feature to support funding requests.

## Recommended remote control software for 4G links
- TelloTerm — https://github.com/SMerrony/telloterm (SMerrony/telloterm) — lightweight terminal/UDP control for scripting and telemetry.
- Tello with JS joystick — https://github.com/st-user/tello-with-js-joystick- (st-user/tello-with-js-joystick-) — browser-based joystick UI that pairs well with tethered / remote links.

## Reverting to stock Tello operation
To restore stock Wi‑Fi operation:
1. Power down the Tello and disconnect any external modules.
2. Physically disconnect the UZ801’s USB power line from the Tello (leave the Tello’s internal wiring intact).
3. Power up the Tello. It should advertise its stock Wi‑Fi SSID and accept connections via the documented Tello Wi‑Fi interface.

Notes and caveats:
- Disconnecting or modifying power wiring can cause bricking or hardware damage if done incorrectly; perform in an isolated bench environment and keep a recovery plan.
- Removing the UZ801 power feed may not revert any persistent firmware changes made to the Tello itself (if you installed modified ROMs); “reverting to stock” by removing external hardware only works when the stock Tello firmware remains intact.
- Warranty and manufacturer support will likely be void after hardware modification.

## Implementation notes: control & protocols
- Simple UDP command interface: The Tello exposes a documented, simple UDP text/command API for flight and telemetry control. This makes rapid prototyping and scripting straightforward.
- MAV compatibility: Tello is not MAVLink-native out of the box, but community projects and bridges exist that translate the Tello UDP API to MAVLink. HandsomeTello intends to provide a stable bridge layer for integration with MAV ecosystems (deferred — see above).

## Security & Responsible Use
This project documents research into microdrone payloads and includes references to the term "microvandalism" as used in academic/white-paper contexts. Important rules:
- This repository is intended for lawful research, academic study, responsible environmental projects, and authorized experimental testing only.
- Do not use the instructions here to perform illegal or harmful activities. The presence of the term "microvandalism" in a white paper does not imply approval for malicious use.
- Regulations and classifications (e.g., "toy drone") differ between jurisdictions and can change over time. Always verify local aviation rules, manufacturer terms of service, and any institutional review or ethics processes that apply before testing or deploying hardware.
- There are public disclosures of vulnerabilities affecting the drone Wi‑Fi chipset. Avoid exposing research devices to untrusted networks, follow upstream advisories, and adopt network isolation / firewalling / patched images when available. We will not publish exploit details in this repository.
- We recommend adding an institutional or project-level ethics statement and a short legal disclaimer in docs/ to accompany any white-paper references.

## Get started
1. Clone this repo
2. Read docs/installation.md for supported hardware and build steps
3. See examples/photogrammetry for an end-to-end payload + capture workflow

## Release / Downloads
We include the OpenStick UZ801 v3.0 bundle as a release asset. Upstream documentation and detailed setup instructions are available at: https://wvthoog.nl/openstick/

Please see RELEASE_NOTES.md for the planned release notes and the SHA256 checksum placeholder for the openstick-uz801-v3.0.zip release asset.

## Project license
This repository uses a split-licensing approach:
- Documentation, designs and media: Creative Commons Attribution-ShareAlike 4.0 International (CC BY‑SA 4.0). See LICENSE for details.
- Software and firmware: MIT License. See LICENSE.code for full text.

Note: CC BY‑SA is not generally recommended for executable code; if you prefer a single license, update LICENSE and LICENSE.code accordingly.

## Credits / Contributors
See CREDITS.md for upstream authors, links to original projects (HandsomeMod, OpenStick), and suggested contributor attribution format.

## Assets / Logos
Place the following images in the `assets/` directory (placeholders are included):
- `assets/cc-by-sa-88x31.png` — Creative Commons BY-SA logo (88×31 px)
- `assets/scivizlab-vienna-logo-120x40.png` — ScivizLab Vienna logo (~120×40 px)

At the bottom of repository pages and the README we display both logos:

<p align="center">
  <a href="https://creativecommons.org/licenses/by-sa/4.0/">
    <img src="assets/cc-by-sa-88x31.png" alt="CC BY-SA 4.0" />
  </a>
  &nbsp;&nbsp;
  <img src="assets/scivizlab-vienna-logo-120x40.png" alt="ScivizLab Vienna" />
</p>

## Contributing
See CONTRIBUTING.md and CODE_OF_CONDUCT.md for how to contribute. When opening PRs related to deferred features, please:
- Add a short feasibility note and a rough cost estimate.
- Include safety/ethics considerations and test plans.
- If code or firmware is included, propose a compatible software license for those components (or confirm they remain under MIT).

## License
Documentation/designs: CC BY‑SA 4.0 — see LICENSE
Code/firmware: MIT — see LICENSE.code
