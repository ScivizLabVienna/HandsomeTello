[![Release](https://img.shields.io/github/v/release/ScivizLabVienna/HandsomeTello?label=release&color=brightgreen)](https://github.com/ScivizLabVienna/HandsomeTello/releases)
[![Docs license](https://img.shields.io/badge/docs-CC%20BY--SA%204.0-lightgrey)](LICENSE)
[![Code license](https://img.shields.io/badge/code-MIT-green)](LICENSE.code)
[![Issues](https://img.shields.io/github/issues/ScivizLabVienna/HandsomeTello)](https://github.com/ScivizLabVienna/HandsomeTello/issues)
[![Contributors](https://img.shields.io/github/contributors/ScivizLabVienna/HandsomeTello)](https://github.com/ScivizLabVienna/HandsomeTello/graphs/contributors)
[![Stars](https://img.shields.io/github/stars/ScivizLabVienna/HandsomeTello?style=social)](https://github.com/ScivizLabVienna/HandsomeTello/stargazers)

# HandsomeTello — The open micro drone

HandsomeTello turns the DJI Tello into an open, hackable micro drone: run lightweight Linux userspace, attach research payloads, and prototype workflows for photogrammetry, environmental sensing, and robotics research.

---

## Table of contents
- [Quick highlights](#quick-highlights)
- [Why Ryze Tello](#why-ryze-tello)
- [Features & roadmap](#features--roadmap)
- [Deferred / Not-included features](#deferred--not-included-features)
- [Recommended remote control software (4G)](#recommended-remote-control-software-4g)
- [Quickstart](#quickstart)
- [Revert to stock](#revert-to-stock)
- [Downloads & releases](#downloads--releases)
- [Attribution & credits](#attribution--credits)
- [Security & Responsible Use](#security--responsible-use)
- [License](#license)
- [Contributing](#contributing)

---

## Quick highlights
- Target hardware: Tello / UZ801-derived WiFi SoC modding  
- Goals: Linux userspace support, modular payloads, photogrammetry-ready toolchain  
- Keywords: OpenStick, UZ801, Tello, photogrammetry, modular-drone, embedded-linux, microdrone

## Why Ryze Tello
- Cheap, mass-produced, and accessible — low cost enables iterative experimentation and larger-scale testing.  
- Open, documented command/telemetry API — simplifies scripting and automation.  
- Established community research and projects to build on — faster reproducibility.  
- Often classified as a toy drone — fewer regulatory barriers in many jurisdictions (verify local rules before testing).

---

## Features & roadmap
Planned and implemented project areas:
- Linux userspace on UZ801 expansion modules
- Modular payload support (camera, environmental sensors)
- Photogrammetry capture examples and pipelines
- Bridge/adapter patterns for MAVLink integration (planned)
- Security hardening and isolation best-practices (planned)

Want a prioritized roadmap? Open an issue labeled `roadmap` or `help wanted` and we’ll triage.

---

## Deferred / Not-Included Features (time & financial constraints)
The following features were scoped but deferred from the initial release. Each is documented so contributors can pick them up.

- vGPS / NAVSOP / Assisted Navigation (cell & Wi‑Fi)
- Arduino Pro Mini via UART — low-power management, solar recharge, autonomous RTH
- Real-time low-bandwidth video transcoding (reduce cellular data fees)
- openipc and/or wifi-broadcast-ng camera streams
- USB‑OTG host on UZ801 (attach SDR, LiDAR, USB sensors)
- Rooting / reverse engineering Tello stock firmware (hardware swaps, native USB/video)
- MAVLink bridges (Tello UDP → MAV)
- Wi‑Fi chipset security remediation / hardening

See the issue tracker for individual tasks and suggested estimates.

---

## Recommended remote control software (4G links)
For remote operation over IP/cellular tunnels we recommend:
- TelloTerm — https://github.com/SMerrony/telloterm — lightweight UDP terminal control and telemetry
- Tello with JS joystick — https://github.com/st-user/tello-with-js-joystick- — browser-based joystick UI

Both are third-party projects — check their repos and licenses before use.

---

## Quickstart
1. Clone the repo:
   git clone https://github.com/ScivizLabVienna/HandsomeTello.git
2. Read docs/installation.md for recommended hardware and the test bench setup.
3. Prepare an isolated test environment (bench power, USB‑serial, isolated Wi‑Fi).
4. Consult CREDITS.md and upstream OpenStick docs before flashing or reimaging.

Commands
```bash
# clone and open
git clone https://github.com/ScivizLabVienna/HandsomeTello.git
cd HandsomeTello
```

---

## Revert to stock
To restore stock Wi‑Fi operation after using the UZ801:
1. Power down Tello and disconnect external modules.
2. Physically disconnect the UZ801’s USB power feed from the Tello (leave internal wiring intact).
3. Power the Tello — it should advertise the stock Wi‑Fi SSID and accept connections.

Caveats:
- If the internal Tello firmware was modified, hardware removal alone may not revert to a truly stock state. Consult upstream OpenStick docs for firmware reflashing steps.
- Hardware modifications may void warranty and can brick devices. Test on expendable units in an isolated lab.

---

## Downloads & releases
We include the OpenStick UZ801 v3.0 bundle as a release asset in our `v0.1` release. Upstream documentation and a detailed setup guide are at:
- https://wvthoog.nl/openstick/

When downloading the release asset, verify the SHA256 checksum included in the release notes.

---

## Attribution & credits
This project builds on community work:
- Handsome UZ801 mod — https://github.com/HandsomeMod  
- Vim Vanthoog / OpenStick — https://wvthoog.nl/openstick/  

See CREDITS.md for full attribution and recommended wording. The OpenStick upstream page contains detailed setup documentation we reference heavily.

---

## Security & Responsible Use
- Report security issues by opening an issue labeled `security` in this repo (see SECURITY.md). Do not post exploit details publicly.  
- This repository documents research that references the term “microvandalism” as used in an associated white paper. The project does not endorse illegal activity — follow institutional and legal requirements.  
- Avoid exposing development devices to untrusted networks and follow the recommendations in SECURITY.md.

---

## License
- Documentation, designs and media: Creative Commons Attribution-ShareAlike 4.0 International (CC BY‑SA 4.0). See LICENSE.  
- Software and firmware: MIT License. See LICENSE.code.

Notes: CC BY‑SA is not ideal for executable code; we use MIT for code/firmware to encourage reuse and contributions.

---

## Contributing
See CONTRIBUTING.md and CODE_OF_CONDUCT.md. When contributing:
- Open an issue for large changes before submitting a PR.
- Include safety/ethics notes for features touching deployment or payloads.
- Specify the intended license for new code if you deviate from MIT.

---

<p align="center">
  <a href="https://creativecommons.org/licenses/by-sa/4.0/">
    <img src="assets/cc-by-sa-88x31.svg" alt="CC BY-SA 4.0" width="88" height="31" />
  </a>
  &nbsp;&nbsp;
  <img src="assets/scivizlab-vienna-logo-120x40.svg" alt="ScivizLab Vienna" width="120" height="40" />
</p>
