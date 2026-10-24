# Changelog

This ROM is for annibale (aka, Redmi K90 and POCO F8 Pro),
Evolution X 12.3 (Android 17), Unofficial.

## 2026-10-23

Initial release.
Base firmware: HyperOS OS3.0.307.0.WPKCNXM CN
Android security patch: 2026-10-01

What's working:

### Display

- Adaptive screen refresh rate 60/90/129.
- Screen cutout: status bar icons perfectly align with front facing camera hole.
- Elongated the autoBrightnessDarkeningLightDebounce to 3000, which may help reduce the
  abrupt screen brightness drop when ambient light changes.

### Connectivity

- Cellular, IMS (VoLTE and SMS), Bluetooth, NFC all work fine.
- Supported showing 5G+ indicator when connected to NR network with Carrier Aggregation.
- Dropped the unique 5G SA indicator. A unified 5G icon will be displayed for both NSA
  and SA networks.

### Camera

- Integrated MIUI Camera: all lenses work fine.
- Supported motion photo (aka, Live Moments).

### Speakers

- Integrated Dolby Atmos sound effect from Lunaris.

### Sensors

- Fixed fingerprint enrollment by loading Xiaomi's `qcom_us` and `goodix_us2` fingerprint
  HAL classes.
- Ambient light sensors work fine.

### Location and Positioning

- Integrated HyperOS's native Xiaomi Metok network location provider.
- Introduced a NLP broker and swticher app, which allows users to select network location
  provider from GMS (default) and Xiaomi Metok. This helps address the location failure
  for users with connection issues to the Google servers (like Mainland China).

