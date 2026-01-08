<p align="center">
  <img src="assets/hero-banner-1200x360.jpg" alt="HandsomeTello — The open micro drone" width="100%" style="max-width:600px;border-radius:8px;" />
</p>

This drone was developed as part of the ongoing research project [KanalOpal](https://www.scivizlab.com/kanal-opal) for the Science Visualization Lab Vienna, University of Applied Arts.

[![Release](https://img.shields.io/github/v/release/ScivizLabVienna/HandsomeTello?label=release&color=brightgreen)](https://github.com/ScivizLabVienna/HandsomeTello/releases)
[![Docs license](https://img.shields.io/badge/docs-CC%20BY--SA%204.0-lightgrey)](LICENSE)
[![Code license](https://img.shields.io/badge/code-MIT-green)](LICENSE.code)
[![Issues](https://img.shields.io/github/issues/ScivizLabVienna/HandsomeTello)](https://github.com/ScivizLabVienna/HandsomeTello/issues)
[![Contributors](https://img.shields.io/github/contributors/ScivizLabVienna/HandsomeTello)](https://github.com/ScivizLabVienna/HandsomeTello/graphs/contributors)
[![Stars](https://img.shields.io/github/stars/ScivizLabVienna/HandsomeTello?style=social)](https://github.com/ScivizLabVienna/HandsomeTello/stargazers)

# HandsomeTello — The open micro drone

HandsomeTello turns the DJI Tello into an open, easily modifiable micro drone: run lightweight Linux userspace, attach research payloads, and prototype workflows for photogrammetry, environmental sensing, and robotics research.

---

## Table of contents
- [Quickstart](#quickstart)
- [Quick highlights](#quick-highlights)
- [Why Ryze Tello](#why-ryze-tello)
- [Features & roadmap](#features--roadmap)
- [Deferred / Not-included features](#deferred--not-included-features)
- [Recommended remote control software (4G)](#recommended-remote-control-software-4g)
- [Revert to stock](#revert-to-stock)
- [Downloads & releases](#downloads--releases)
- [Attribution & credits](#attribution--credits)
- [Security & Responsible Use](#security--responsible-use)
- [License](#license)
- [Contributing](#contributing)

---
## Quickstart
1. Clone the repo:
   git clone https://github.com/ScivizLabVienna/HandsomeTello.git
2. Follow the instructions on  [https://wvthoog.nl/openstick/](https://wvthoog.nl/openstick/)
3. Follow the instructions on [https://instructables.com/HandsomeTello/](https://www.instructables.com/HandsomeTello/)
4. Fly
---
## Quick highlights
- Target hardware: Tello / UZ801-derived WiFi dongle
- Goals: Linux userspace support, modular payloads, photogrammetry-ready toolchain  
- Keywords: OpenStick, UZ801, Tello, photogrammetry, modular-drone, embedded-linux, microdrone

## Why Ryze Tello
- Cheap, mass-produced, and accessible — low cost enables iterative experimentation and larger-scale testing.  
- Open, documented command/telemetry API — simplifies scripting and automation.  
- Established community research and projects to build on — faster reproducibility.  
- Classified as a toy drone — fewer regulatory barriers in many jurisdictions (verify local rules before testing).

---

## Features
Planned and implemented project areas:
- Linux userspace on UZ801 expansion modules
- Modular payload support (camera, environmental sensors)
- Photogrammetry capture examples and pipelines
- Bridge/adapter patterns for MAVLink integration

Want a prioritized roadmap? Open an issue labeled `roadmap` or `help wanted` and we’ll triage.

---

## Deferred / Not-Included Features (time & financial constraints)
The following features were scoped but deferred from the initial release. Each is documented so contributors can pick them up.

- vGPS / NAVSOP / Assisted Navigation (cell & Wi‑Fi)[https://www.wired.com/story/finding-your-way-without-gps/](https://web.archive.org/web/20250718205549/https://www.wired.com/story/finding-your-way-without-gps/)

- Arduino Pro Mini via UART — low-power deep sleep, solar recharge, autonomous RTH https://the-diy-life.com/making-an-ultra-low-power-arduino-pro/ https://shop.halocell.energy/products/halocell-ambient-module-60x23_4

- Real-time low-bandwidth video transcoding (reduce cellular data fees)
  https://heavydeck.net/post/64k-is-enough-for-video/

- openipc and/or wifi-broadcast-ng (needs firmware modification of WIFI SoC)
  https://github.com/MrJabu/RyzeTelloFirmware
  https://github.com/OpenIPC https://github.com/OpenIPC/wfb-ng-openwrt

- USB‑OTG host on UZ801 (attach SDR, LiDAR, USB sensors)
  https://wiki.postmarketos.org/wiki/Zhihe_series_LTE_dongles_(generic-zhihe)

- Rooting / reverse engineering Tello stock firmware (hardware swaps, native USB/video)
  https://github.com/MrJabu/RyzeTelloFirmware

- MAVLink bridges (Tello UDP → MAV)
  https://mavlink.io/

- Wi‑Fi chipset security remediation / hardening
  https://www.cve.org/CVERecord?id=CVE-2019-6496

See the issue tracker for individual tasks and suggested estimates.

---

## Recommended remote control software (4G links)
For remote operation over IP/cellular tunnels we recommend:
- TelloTerm — https://github.com/SMerrony/telloterm — lightweight UDP terminal control and telemetry
- Tello with JS joystick — https://github.com/st-user/tello-with-js-joystick- — browser-based joystick UI

Both are third-party projects — check their repos and licenses before use.

---

## Future directions

As of yet there is no further development planned on this project therefore we encourage you to fork and modify and share to your hearts content.

Flapping wing drones have become affordable, sophisticated and widespread enough to be used as a viable artistic and research platform.

In terms of efficiency, noise pollution, aesthetics and non intrusiveness, flapping wing drones far outmatch propeller driven micro air vehicles. Especially in an urban environment. 
One of the highly recommended platforms (still in pre-launch at the time of this writing) would be the swift from the french company bionic bird.

https://www.kickstarter.com/projects/274008848/the-swift-natural-flight-reinvented
---
