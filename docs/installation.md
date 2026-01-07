# Installation (overview)

This document is a short installation and build overview. For detailed step-by-step procedures, check the docs/ folder and issue tracker for platform-specific guides.

Prerequisites
- A Ryze Tello unit (recommended stock version)
- UZ801 expansion hardware where applicable (see CREDITS for upstream mod links)
- A Linux host for toolchains and flashing (Ubuntu/Debian recommended)
- USB serial adapters, power meter, and spare batteries for testing

Quickstart
1. Clone the repository:
   git clone https://github.com/ScivizLabVienna/HandsomeTello.git
2. Review CREDITS.md and confirm upstream assets/ROM licenses.
3. Prepare a test bench: USB-serial adapter, power monitor, and an isolated Wi‑Fi network for safe trials.
4. Follow the hardware-specific guide (TBD — filed as issues). See examples/photogrammetry for an example workflow.

Caveats
- Do not connect exposed hardware to production or untrusted networks during early development.
- Verify local regulations before outdoor testing.

(Expand this page with step-by-step flashing instructions, serial pinouts, BOM, and required toolchain commands. We can draft those next once you provide upstream ROM links and hardware schematics.)
