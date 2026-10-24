# Evolution X for Redmi K90 / POCO F8 Pro

Unofficial Evolution X releases for Redmi K90 / POCO F8 Pro
(codename: `annibale`).

This project is not affiliated with Xiaomi, POCO, or the Evolution X project.

## Releases

Published downloads and checksums will be listed on the
[Releases](https://github.com/soytony/evolution-x-annibale-releases/releases) page.
No release assets have been published yet.

Read the [2026-10-23 installation guide](docs/20261023/README.md) and
[changelog](CHANGELOG.md) before flashing.

## Current Build

| Field | Value |
| --- | --- |
| Version | Evolution X 12.3 Unofficial |
| Build date | 2026-10-23 |
| Device | Redmi K90 / POCO F8 Pro (`annibale`) |
| Android version | 17 |
| Android security patch | 2026-10-01 |
| Google services | Included |
| Stock firmware base | HyperOS `OS3.0.307.0.WPKCNXM`, Android 16, CN |
| Validation | CN hardware validated with development images; the exact signed release has not been boot tested |

Only CN hardware has been validated. Other variants, including the global
POCO variant, have not been validated. The installer bundles the required
stock firmware and flashes it before the Android images.

## Installation

1. Back up important data and remove Google accounts before installation.
2. Unlock the bootloader.
3. Download the fastboot ZIP and verify its published SHA-256 checksum.
4. Extract the complete bundle and start the phone in bootloader fastboot.
5. Run `./flash-all.sh` on Linux/macOS or `flash-all.bat` on Windows.
6. Follow the prompts. After all partitions flash successfully, enter exactly
   `WIPE_USERDATA` to erase userdata and metadata. Any other response preserves
   both and continues to reboot.

The installer targets Android slot A and replaces the logical partitions.
The bundled firmware requires stock antirollback version 1; newer or unknown
versions are rejected. Do not relock the bootloader after installation.
AVB verification remains disabled.

See the [complete installation guide](docs/20261023/README.md) for compatibility,
firmware mapping, prerequisites, and installer behavior.

## Google Apps

Google services and apps are included. Do not flash a separate GApps package.

## Source and Issues

- [Evolution X](https://github.com/Evolution-X)
- [Device tree](https://github.com/soytony/android_device_xiaomi_annibale)
- [Vendor tree](https://github.com/soytony/proprietary_vendor_xiaomi_annibale)

Report reproducible issues through this repository's
[issue tracker](https://github.com/soytony/evolution-x-annibale-releases/issues).
Include the build version, device variant, clean or dirty installation status,
steps to reproduce, and relevant logs. Remove personal data, account details,
and device serial numbers before posting.
