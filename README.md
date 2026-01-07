This drone was developed as part of the ongoing research project KanalOpal for the Science Visualization Lab Vienna, University of Applied Arts Vienna.


[![Build Status](https://img.shields.io/github/actions/workflow/status/ScivizLabVienna/HandsomeTello/ci.yml?branch=main&style=flat-square)](https://github.com/ScivizLabVienna/HandsomeTello/actions)
[![Releases](https://img.shields.io/github/v/release/ScivizLabVienna/HandsomeTello?style=flat-square)](https://github.com/ScivizLabVienna/HandsomeTello/releases)
[![License](https://img.shields.io/github/license/ScivizLabVienna/HandsomeTello?style=flat-square)](LICENSE)


# HandsomeTello

![Hero banner: HandsomeTello](assets/hero-banner.png)

A research and development fork of the Ryze Tello drone platform, adapted and extended by the Science Visualization Lab Vienna for creative, educational and research uses. This repository collects firmware, configuration guidance, companion tools and documentation to support the HandsomeTello project.

Table of contents
- [Quick highlights](#quick-highlights)
- [Why Ryze Tello](#why-ryze-tello)
- [Features & roadmap](#features--roadmap)
- [Deferred features](#deferred-features)
- [Recommended remote control software](#recommended-remote-control-software)
- [Quickstart](#quickstart)
- [Revert to stock](#revert-to-stock)
- [Downloads & releases](#downloads--releases)
- [Attribution & credits](#attribution--credits)
- [Security & Responsible Use](#security--responsible-use)
- [License](#license)
- [Contributing](#contributing)


## Quick highlights
- Base platform: Ryze Tello (cheap, programmable, safe for indoor use)
- Purpose: research, visualization, creative coding, and classroom demonstrations
- What’s included: documentation, recommended apps, firmware/config tips, and flight workflows
- Target users: researchers, students, educators, artists


## Why Ryze Tello
The Ryze Tello is an affordable, lightweight drone with a programmable SDK, making it an excellent candidate for exploratory research and education. It offers safe indoor flight characteristics, a stable flight controller, and a developer API that is sufficient for basic autonomy, positioning experiments and media capture.

Key reasons we picked it:
- Low cost and easy replacement
- Open-ish SDK for programmatic control
- Lightweight and safe for lab / classroom environments
- Strong community and available tooling


## Features & roadmap
Current implemented features:
- Documentation for common modding workflows
- Recommended companion software and control options
- Quickstart guide for flashing and configuration
- Safety and legal guidance for research use

Roadmap (planned/ongoing):
- Improved flight-stability tuning profiles for indoor environments
- Simple computer-vision assisted position-holding examples
- Companion mobile/web app prototypes for experiment control
- Automated test harnesses for reproducible flight experiments
- Integration examples for ROS/other robotics stacks

If you plan on contributing a feature, open an issue to discuss design and safety implications first.


## Deferred features
The following are intentionally deferred until we have the necessary safety approvals and testing infrastructure:
- High-speed autonomous flight routines
- Payload delivery mechanisms
- Long-range modifications that alter RF compliance


## Recommended remote control software
Depending on your use case, select one of the following:
- Tello EDU App (official) — simple, reliable, good for basic teaching
- TelloPy — Python SDK wrapper for scripted flights and research experiments
- Dronecode/Node-based interfaces — for web or node-based control prototypes

Always test in a controlled environment and follow the safety guidance in this README.


## Quickstart
1. Unbox and inspect the drone for visible damage.
2. Charge the original battery and update the official Tello firmware via the official app if necessary.
3. Connect to the Tello Wi‑Fi network from your laptop or phone.
4. Use one of the recommended control software packages (Tello EDU, TelloPy, etc.) to run basic takeoff/land and hover tests.

Minimal example using TelloPy (Python):

```python
from tellopy import Tello

drone = Tello()
drone.connect()
drone.wait_for_connection(60.0)
drone.takeoff()
import time
time.sleep(3)
drone.land()
```

Note: the example above is illustrative; see TelloPy docs for installation and usage details.


## Revert to stock
If you performed firmware or configuration changes and need to revert to stock behavior:
1. Remove any attached hardware (custom mounts, extra sensors) that may affect boot or safety.
2. Use the official Tello app to check and re-apply the manufacturer's firmware update.
3. If you flashed custom firmware, consult the flash tool’s documentation for an official re-flash method. If in doubt, reach out on our project issue tracker for guidance.


## Downloads & releases
Official releases and binary assets are attached to GitHub releases for this repository. Check the Releases page for the latest supported downloads:

https://github.com/ScivizLabVienna/HandsomeTello/releases

If you publish build artifacts or firmware images, include checksums and clear instructions for use.


## Attribution & credits
This drone was developed as part of the ongoing research project KanalOpal for the Science Visualization Lab Vienna, University of Applied Arts Vienna.

Contributors and acknowledgements:
- Science Visualization Lab Vienna — project lead and maintainers
- Students, researchers and community contributors — see the CONTRIBUTORS file or Git history
- External libraries: TelloPy, OpenCV, and other community projects used in examples

If you used material from another project, please add appropriate attribution and license notes.


## Security & Responsible Use
Safety first:
- Operate in clear, controlled spaces and follow all local regulations for drone operation.
- Never fly over people, crowds, or restricted areas.
- For experiments that involve autonomy or perception, maintain a manual override and test at low speeds and altitudes.
- If modifying RF hardware or antennas, ensure compliance with local radio regulations.

Responsible research:
- Consider privacy implications when recording or streaming video.
- Avoid collecting personal data without consent and use anonymization where applicable.

If you discover a security vulnerability in this project, please report it privately to the maintainers via the repository's security contact (or open an issue labeled SECURITY if appropriate).


## License
See the LICENSE file in this repository for full license terms.


## Contributing
We welcome contributions. Please follow these steps:
1. Open an issue to discuss major changes or new features.
2. Fork the repository and create a feature branch for your work.
3. Keep commits focused and include descriptive messages.
4. Open a pull request against the main branch; include screenshots, logs or recordings for UI/behavior changes and tests where possible.
5. Ensure you sign-off or follow the contributor license process described in CONTRIBUTING.md if applicable.

Code of conduct: please be respectful and follow the community guidelines.


---

If anything in this README needs to be restored further or you want content phrased differently, tell me what to change and I will update the file.