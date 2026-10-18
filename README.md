# postmarketOS — Motorola Moto G45 5G (fogos)

Downstream postmarketOS device and kernel packages for the **Motorola Moto G45 5G**, codename `fogos`.

> **Status: Work in Progress :)**

## Overview

This repository contains the device and kernel packages for bringing postmarketOS to the Motorola Moto G45 5G.

| Package | Description |
|---|---|
| `device-motorola-fogos` | Device metadata, boot configuration, and initramfs modules |
| `linux-motorola-fogos` | Downstream kernel package, configuration, and compatibility patches |

## Device information

| Property | Details |
|---|---|
| Device | Motorola Moto G45 5G |
| Codename | `fogos` |
| Architecture | AArch64 |
| SoC | Qualcomm Snapdragon 695 5G |
| Platform | SM6375 |
| Kernel | Linux 5.4.302 |
| Kernel configuration | `holi-qgki_defconfig` |

## Kernel source

The kernel is maintained in a separate repository.

- **Repository:** [android_kernel_motorola_sm6375](https://github.com/reyaansh72/android_kernel_motorola_sm6375)
- **Branch:** `postmarketos-motorola-fogos`
- **Pinned commit:** [`6ad40bbece9c25275752c07e1fb9320c37425fe5`](https://github.com/reyaansh72/android_kernel_motorola_sm6375/commit/6ad40bbece9c25275752c07e1fb9320c37425fe5)

## Kernel configuration

The kernel fork's `arch/arm64/configs/vendor/holi-qgki_defconfig` has been adjusted for postmarketOS.

Relevant options include:

```text
CONFIG_VT=y
CONFIG_VT_CONSOLE=y
```

These enable virtual terminal and console support for text-based output and debugging.

## Building

Build the packages using [pmbootstrap](https://postmarketos.org/pmbootstrap/).

**Build the kernel:**

```bash
pmbootstrap build linux-motorola-fogos
```

**Build the device package:**

```bash
pmbootstrap build device-motorola-fogos
```

**Generate the installation artifacts:**

```bash
pmbootstrap install
```

`pmbootstrap install` prepares the root filesystem and installation artifacts; it does not automatically flash the device.

## Development notes

During kernel preparation, the build encountered a GCC compatibility header error involving `include/linux/compiler-gcc.h`.

The postmarketOS community helped identify the archived Samsung downstream kernel package as a useful reference:

`device/archived/linux-samsung-beyond2lte-downstream/APKBUILD`

The suggested adjustment involved `REPLACE_GCCH=0` in the kernel build process. This project follows that guidance while kernel build and device functionality continue to be tested.

## Acknowledgements

Special thanks to **[@longnoserob:matrix.org](https://matrix.to/#/@longnoserob:matrix.org)** for helping investigate the kernel build failure, reviewing the error logs, and pointing me toward the Samsung downstream kernel reference and the `REPLACE_GCCH=0` fix.

Your help made a real difference in getting this port unstuck. Thank you!

Thanks to the **postmarketOS community** for its documentation, existing ports, and continued knowledge sharing.

Use experimental images at your own risk and ensure you have an appropriate recovery procedure before attempting to boot or flash them.

## License

See the individual package metadata and kernel source repository for applicable licensing terms.
