# Uke Linux images

Fedora AArch64 image publication for Xiaomi Pad 7 and POCO Pad X1 (`uke`, SM7675).

**Current status:** the [Fedora Core prebuild test with signed kernel 1.17](https://github.com/MCC45TR/uke-linux-images/releases/tag/prebuild-fedora-core-20261012-copr1.17)
provides boot/root images, checksums, source/package identities and installation
limits. The exact boot image reaches the owner's existing EXT4 root by RAM boot;
the clean released root image has only host and generic VM qualification.
The exact boot image has two RAM starts and a full boot_b write/readback while
stock A remains selected. Firmware DRM supplies software scanout and paired
normal brightness writes have matching readbacks; optical confirmation and
native Adreno acceleration remain open. This is an experimental console
system. A private original Fedora KDE copy is undergoing physical installation;
its separate sanitized public image remains under validation.

A separate stock-ABL development route prepares `fedora_boot.img` for `boot_b`
and `system.img` for an independently prepared GPT `linux` partition. It uses a
root-capable built-in initramfs, runtime stock-DT adaptation and a local TTY1
screen candidate while Aloha remains under development. Run
`./ukelinux.sh --build boot-pair --distro=fedora --help` from the workspace.
The [October 9 validation record](https://github.com/MCC45TR/uke-fedora-builder/blob/test/stock-abl-core-pair/reports/FEDORA-BOOT-PAIR-2026-10-09.json)
qualifies the local pair: Image/modules, EXT4/SELinux, full sparse decoding,
generic VM real-root/TTY execution and both wrong-root rejection cases passed.
The 96 MiB boot image and 556.23 MiB sparse system image (3 GiB logical EXT4)
were the October 9 coordinated owner-test candidate. Later physical development
reached a screen TTY and automatic USB/Wi-Fi SSH. The current release records
its separate RAM, root-image and peripheral limits. This stock-ABL route requires
no ESP and performs no partition creation, flashing or slot activation.

| Resource | Location |
|---|---|
| Published image assets | [GitHub Releases](https://github.com/MCC45TR/uke-linux-images/releases) |
| Image construction | [uke-fedora-builder](https://github.com/MCC45TR/uke-fedora-builder) |
| Kernel packages | [senemos-uke-kernel-mainline](https://github.com/MCC45TR/senemos-uke-kernel-mainline) |
| Platform packages | [uke-linux-hardware-support](https://github.com/MCC45TR/uke-linux-hardware-support) |
| Project status | [uke-linux](https://github.com/MCC45TR/uke-linux) |
| Engineering records | [Private documentation](https://github.com/MCC45TR/uke-linux-docs) |

Each release must provide checksums, a package/source manifest, kernel
and DTB identity, filesystem sizes, exact device/firmware scope, installation
and rollback requirements, and separate static, emulation and physical results.
Images will use Uke evidence for `uke_esp` and `uke_linux` roles. Nabu geometry,
boot binaries, firmware and calibration are not portable inputs.

KDE desktop applications must come from the original distribution. No cloned,
forked or rebuilt KDE application variants are published. The owner permits
Python only for original signed Fedora KDE dependencies. Core, early initramfs
and project startup/service/test helpers retain their strict native policy.

This independent community project is not an official Fedora or Xiaomi product.

The separate UEFI Core profile uses ESP32-S3 HID shell input on VT2 and CDC journal
output with the tablet acting as USB host. It opens an explicit local development
root shell; this profile is unsuitable as a general-purpose security default.
The existing bridge firmware, Uke USB/UFS DT support, UEFI handoff and measured
partition geometry still require independent acceptance. The published
stock-ABL profile instead uses direct-PC ACM/ECM. Neither debug profile is a
general-purpose security default. Construction starts
with `ukelinux.sh` in the workspace; see the [Core image guide](https://github.com/MCC45TR/uke-fedora-builder/blob/main/docs/IMAGES.md).

The [first local filesystem candidate](https://github.com/MCC45TR/uke-fedora-builder/blob/main/reports/CORE-FILESYSTEM-2026-10-05.json)
passed complete root/initramfs, EXT4/ESP and UKI byte-match checks. Its kernel
report retains its historical missing enabled USB/UFS and static RAM findings;
it does not describe the later stock-ABL RAM result or current prebuild assets.
