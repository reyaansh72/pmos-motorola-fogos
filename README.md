# postmarketOS — Motorola Moto G45 5G (fogos)

Downstream postmarketOS device and kernel packages for the
Motorola Moto G45 5G, codename **fogos**.

> **Status: Work in progress.** This port is under development.
> Successful package checksums do not imply that the kernel boots
> or that hardware support has been tested.

## Repository contents

| Package | Purpose |
|---|---|
| `device-motorola-fogos/` | Device metadata, boot image settings, and initramfs module list |
| `linux-motorola-fogos/` | Downstream kernel APKBUILD, kernel config, and compatibility patches |

## Kernel source

The kernel source is maintained separately:

- Repository: https://github.com/reyaansh72/android_kernel_motorola_sm6375
- Port branch: `postmarketos-motorola-fogos`
- Pinned commit: `6ad40bbece9c25275752c07e1fb9320c37425fe5`
- Branch: `pmos-motorola-fogos`

## Kernel configuration

The kernel fork's `arch/arm64/configs/vendor/holi-qgki_defconfig`
has been edited to enable:

```text
CONFIG_VT=y
CONFIG_VT_CONSOLE=y
