# Uke Linux images

Fedora AArch64 images for Xiaomi Pad 7 and POCO Pad X1 (`uke`, SM7675).

## Fedora Rawhide Alpha 1 — 15 October 2026

Alpha 1 is published in the main project:
[release files and checksums](https://github.com/MCC45TR/uke-linux/releases/tag/fedora-rawhide-alpha-1).
**Experimental alpha — not suitable for daily use.**

The public boot and root files are rebuilt from the normal Linux 7.2.9 revision
1.39 software baseline; these exact files have not been booted on the tablet.
Unapproved OEM firmware, calibration and device identities are excluded. A
firmware provisioning method is not yet available, so dependent functions may
be unavailable. The `userdata` boot variant is particularly experimental and
replacing Android userdata erases Android user data. Installation instructions
will follow. See the [reporting guide](https://github.com/MCC45TR/uke-linux/blob/main/CONTRIBUTING.md)
and [current hardware table](https://github.com/MCC45TR/uke-linux#hardware-support).

## Project status — 14 October 2026

[Core](https://github.com/MCC45TR/uke-linux-images/releases/tag/prebuild-fedora-core-20261012-copr1.17)
and [original Fedora KDE](https://github.com/MCC45TR/uke-linux-images/releases/tag/prebuild-fedora-kde-20261012-copr1.17)
are available as prebuild tests with kernel revision 1.17, matching boot/root
files and checksums. These exact published root images have passed host and
filesystem checks, but have not been booted on the tablet. Read each release's
installation and rollback notes before testing.

A separate development installation reaches the console and software KDE
desktop, with Wi-Fi SSH and battery readings. This is not the same filesystem
as the public images. Finger input and ten simultaneous touch contacts worked
in the 14 October tablet test. Power and volume buttons and manual backlight
control also worked. Backlight adjustment is linear and difficult to use
comfortably; a logarithmic curve is planned. GPU acceleration, Bluetooth, audio
and USB host mode remain incomplete. See the [current hardware table](https://github.com/MCC45TR/uke-linux#hardware-support).

KDE applications are Fedora's originals. Unmodified Fedora desktop packages may
retain their original Python dependencies. This exception does not cover project
tools, recovery or initramfs payloads. No KDE application is cloned or rebuilt to
change its dependencies.

## Images and boot routes

The stock Android bootloader route produces `fedora_boot.img` for `boot_b` and
`system.img` for a separately prepared GPT partition named `linux`.
The current recipe uses `PARTLABEL=linux`, not a fixed UUID. It does not need
an ESP or Project Aloha, and does not create partitions or flash the tablet.

From the [workspace](https://github.com/MCC45TR/uke-linux):

```sh
./ukelinux.sh --build boot-pair --distro=fedora --help
./ukelinux.sh --check-device --pair DELIVERY_DIRECTORY
```

Normal slot-B startup is not reliable yet; development uses reviewed RAM boots.
Keep Android slot A and a verified Linux rollback. The older initramfs-only
`--build boot` target is a debug image, not a root-capable Fedora installation.

The separate UEFI/ESP32-S3 debug profile is planned. UEFI boot, USB host power
and the bridge still need testing. Debug shells are development features,
not general-purpose security defaults.

## Sources and records

| Resource | Location |
|---|---|
| Image files and checksums | [GitHub Releases](https://github.com/MCC45TR/uke-linux-images/releases) |
| Image recipes and historical checks | [uke-fedora-builder](https://github.com/MCC45TR/uke-fedora-builder) |
| Kernel RPMs | [senemos-uke-kernel-mainline](https://github.com/MCC45TR/senemos-uke-kernel-mainline) |
| Platform packages | [uke-linux-hardware-support](https://github.com/MCC45TR/uke-linux-hardware-support) |
| Image guide | [IMAGES.md](https://github.com/MCC45TR/uke-fedora-builder/blob/main/docs/IMAGES.md) |
| Engineering records | [Private documentation](https://github.com/MCC45TR/uke-linux-docs) |

Each release records checksums, source/package versions, kernel/DTB identity,
filesystem size, device/firmware scope, installation and rollback requirements.
Host, VM and tablet results are listed separately. Nabu partition sizes, boot
binaries and calibration are not used as Uke inputs.

This is an independent community project, not an official Fedora or Xiaomi product.

Documentation and release notes follow the [report style](CONTRIBUTING.md).
