# Redmi K90 / POCO F8 Pro (annibale) — Evolution X 12.3 / Android 17

## Release metadata

| Field | Value |
| --- | --- |
| Device | Redmi K90 / POCO F8 Pro, `annibale` |
| Other variants | Not validated; device tree advertises POCO `2510DPC44G` |
| ROM | Evolution X 12.3, Android 17, GMS included |
| Android security patch | 2026-10-01 |
| Kernel | `6.6.118-android15-8-ge56cf6b09cca-ab15511674-4k` |
| Vendor security patch | 2026-02-01 |
| Firmware base | HyperOS `OS3.0.307.0.WPKCNXM`, Android 16, CN, 20260723 |
| Stock antirollback | 1; installer rejects a device with newer/unknown antirollback |
| Build | `lineage_annibale-cp2a-userdebug`, current workspace with local modifications; build EvolutionX-17.0-20261023-annibale-12.3-Unofficial; build EvolutionX-17.0-20261023-annibale-12.3-Unofficial; build EvolutionX-17.0-20261023-annibale-12.3-Unofficial |
| Source snapshot | Rebuild revisions and local diffs recorded in `source-preflight.json` and final manifest |
| Signing | Evo native build-time signing with existing RoadSTR identities; certificate subject remains `RoadSTR LineageOS`; no post-build re-signing |
| AVB | Images signed with SHA256_RSA4096; verification and hashtree verification disabled by root vbmeta flags 3 |
| AVB root public SPKI DER SHA-256 | `1b946a629cbca7cac05ccc08c5d54b35c261c1ed2866f1d80862eb16b37fc224` |
| AVB system public SPKI DER SHA-256 | `20083fd1169a881ded813631164ab914433278fc5761d6beedeb914e11a93ec1` |
| Test status | Development build: camera capture, both NLP providers and fingerprint enrollment/authentication verified. Exact signed release not boot tested. |
| Known limitations | CN hardware only validated; biometric cancellation lifecycle warnings remain in development logs; logical partitions replaced; userdata wipe optional. |

## Bundle contents

- `images/`: `boot.img`, `init_boot.img`, `dtbo.img`, `recovery.img`,
  `vendor_boot.img`, `vbmeta.img`, `vbmeta_system.img`, `super_empty.img`,
  `odm.img`, `product.img`, `system.img`, `system_dlkm.img`, `system_ext.img`,
  `vendor.img`, `vendor_dlkm.img`. All originate from the same signed
  target-files; `super_empty.img` initializes logical partition metadata.
- `firmware/OS3.0.307.0.WPKCNXM/`: exactly the firmware files below.
- `tools/linux/`, `tools/darwin/`, `tools/windows/`: platform-tools 37.0.0,
  including adb, fastboot, associated files and licenses from the RoadSTR template.
- `flash-all.sh`, `flash-all.bat`, `README.md`, `CHANGELOG.md`,
  `RELEASE-MANIFEST.json`, `FIRMWARE-MANIFEST.json`, `SHA256SUMS`.

Signed target-files and signed image ZIP are separate companion archives,
not nested inside this bundle. No OTA or GApps archive is included.

### Mandatory stock firmware mapping

All files use version OS3.0.307.0.WPKCNXM. All listed files are flashed, in
order, before any Android image. `_ab` partition aliases are retained exactly
from the stock script; these aliases update both firmware slots. Non-slotted
names are also retained exactly. Android images target slot A only.

| Source filename | Fastboot partition | Order |
| --- | --- | --- |
| `abl.elf` | `abl_ab` | 1 |
| `xbl_s.melf` | `xbl_ab` | 2 |
| `xbl_config.elf` | `xbl_config_ab` | 3 |
| `cpucp_dtbs.elf` | `cpucp_dtb_ab` | 4 |
| `pdp_cdb.elf` | `pdp_cdb_ab` | 5 |
| `sdi.mbn` | `soccp_debug_ab` | 6 |
| `dcd.mbn` | `soccp_dcd_ab` | 7 |
| `pdp.elf` | `pdp_ab` | 8 |
| `xbl_sc_test_mode.bin` | `xbl_sc_test_mode` | 9 |
| `shrm.elf` | `shrm_ab` | 10 |
| `aop.mbn` | `aop_ab` | 11 |
| `aop_devcfg.mbn` | `aop_config_ab` | 12 |
| `tz.mbn` | `tz_ab` | 13 |
| `devcfg.mbn` | `devcfg_ab` | 14 |
| `featenabler.mbn` | `featenabler_ab` | 15 |
| `hypvmperformance.mbn` | `hyp_ab` | 16 |
| `uefi.elf` | `uefi_ab` | 17 |
| `uefi_sec.mbn` | `uefisecapp_ab` | 18 |
| `spu_service.mbn` | `spuservice_ab` | 19 |
| `NON-HLOS.bin` | `modem_ab` | 20 |
| `MODEM-FW.bin` | `modemfirmware_ab` | 21 |
| `BTFM.bin` | `bluetooth_ab` | 22 |
| `dspso.bin` | `dsp_ab` | 23 |
| `keymint.mbn` | `keymaster_ab` | 24 |
| `qupv3fw.elf` | `qupfw_ab` | 25 |
| `multi_image.mbn` | `multiimgoem_ab` | 26 |
| `multi_image_qti.mbn` | `multiimgqti_ab` | 27 |
| `cpucp.elf` | `cpucp_ab` | 28 |
| `storsec.mbn` | `storsec` | 29 |
| `tools.fv` | `toolsfv` | 30 |
| `XblRamdump.elf` | `xbl_ramdump_ab` | 31 |
| `imagefv.elf` | `imagefv_ab` | 32 |
| `pvmfw.img` | `pvmfw_ab` | 33 |
| `countrycode.img` | `countrycode_ab` | 34 |
| `vm-bootsys.img` | `vm-bootsys_ab` | 35 |
| `idmanager.mbn` | `idmanager_ab` | 36 |

Mapping provenance: the user-provided stock package's `flash_all.sh`.
The original package had no upstream SHA-256 manifest; local source hashes
were recorded before building and rechecked before copying. The source path,
hashes, exclusions and reasons are in `FIRMWARE-MANIFEST.json`.

Stock Android system/boot/data images, CRC tables, log filesystem reset,
stock rescue image and misc reset are excluded. They are not needed for this
custom ROM installation. Stock bootloader relocking commands are excluded.

## Prerequisites and compatibility

Use annibale CN with an already unlocked bootloader. Back up everything and
remove Google accounts before installation to avoid Factory Reset Protection
problems. Charge the phone and use a reliable USB cable. Do not relock the
bootloader after installing this ROM.

The bundled CN firmware is installed unconditionally. Do not use this package
on a device with antirollback newer than 1 or on another device/region.
Firmware/kernel Android 16/15 identifiers describe the vendor base; the ROM
itself is Android 17. The exact signed release needs device boot validation.

Recovery retains the current development ADB configuration (`ro.adb.secure=0`).

This package reinitializes super metadata and cannot preserve the previous
logical installation as a fallback. After all firmware and Android images flash,
the installer offers an optional userdata/metadata wipe. Enter exactly
`WIPE_USERDATA` to erase them. Any other response preserves userdata and
metadata and continues to reboot. Because this release uses the existing
RoadSTR signing identities, it does not require a wipe for a signing-key change.

## Integrity verification

On Linux:

```sh
sha256sum -c SHA256SUMS
```

On macOS:

```sh
shasum -a 256 -c SHA256SUMS
```

The installer checks SHA-256 for flashable `images/` and `firmware/` payloads
only. Tools, scripts, documents, manifests and complete/companion ZIP archives
are not checksummed. If verification cannot complete, the installer displays
`Continue with unverified images/firmware? [y/N]`; only `y`/`Y` continues.
Missing required payload files always abort before flashing.

## Installation

Extract the complete ZIP. Start the phone in **bootloader fastboot**, not
fastbootd. Connect exactly one fastboot device. The scripts select that
serial, verify `product=annibale`, unlocked status, active slot, antirollback,
and absence of pending OTA snapshots before flashing.

Linux or macOS, from the extracted directory:

```sh
chmod +x flash-all.sh
./flash-all.sh
```

Windows, from Command Prompt in the extracted directory:

```bat
flash-all.bat
```

The Windows batch entry uses built-in Windows PowerShell 5.1 or newer and
bundled fastboot. No Python or separately installed Android tools are needed.

The scripts ask to continue and confirm flashing the identified device.
After every firmware and Android partition flashes successfully, they ask
whether to wipe data. Only exact uppercase `WIPE_USERDATA` erases userdata
and metadata; empty input or any other text preserves both and continues to reboot.
The scripts perform:

1. The complete ordered stock firmware phase in bootloader fastboot.
2. Select Android slot A; flash boot, init_boot, dtbo, recovery, vendor_boot,
   vbmeta and vbmeta_system to their `_a` partitions.
3. Wipe super metadata with `super_empty.img`, then reboot into fastbootd.
4. Flash odm, product, system, system_dlkm, system_ext, vendor and vendor_dlkm
   to their `_a` logical partitions.
5. Optionally erase userdata and metadata after all flashes; require exact
   `WIPE_USERDATA`. Otherwise preserve both. Then select slot A and reboot.

The installer stops at the first failed command. Do not unplug the device
while firmware is flashing. It never locks or unlocks the bootloader.
AVB verification stays disabled through vbmeta flags 3; no verification-
disabling fastboot switches or separate patching steps are needed.

