# Uke Linux images

Fedora AArch64 image publication for Xiaomi Pad 7 and POCO Pad X1 (`uke`, SM7675).

**Current status:** release infrastructure is being prepared. No Fedora system
image has been published or accepted for tablet boot. The first target is a
Fedora Rawhide Core development system, with independent ESP and Linux filesystem images.

| Resource | Location |
|---|---|
| Published image assets | [GitHub Releases](https://github.com/MCC45TR/uke-linux-images/releases) |
| Image construction | [uke-fedora-builder](https://github.com/MCC45TR/uke-fedora-builder) |
| Kernel packages | [senemos-uke-kernel-mainline](https://github.com/MCC45TR/senemos-uke-kernel-mainline) |
| Platform packages | [uke-linux-hardware-support](https://github.com/MCC45TR/uke-linux-hardware-support) |
| Project status | [uke-linux](https://github.com/MCC45TR/uke-linux) |
| Engineering records | [Private documentation](https://github.com/MCC45TR/uke-linux-docs) |

Each future release must provide checksums, a package/source manifest, kernel
and DTB identity, filesystem sizes, exact device/firmware scope, installation
and rollback requirements, and separate static, emulation and physical results.
Images will use Uke evidence for `uke_esp` and `uke_linux` roles. Nabu geometry,
boot binaries, firmware and calibration are not portable inputs.

KDE desktop applications must come from the original distribution. No cloned,
forked or rebuilt KDE application variants are published. Graphical admission
remains blocked by incompatible Python payloads under the Uke target policy.

This independent community project is not an official Fedora or Xiaomi product.

The Core candidate profile uses ESP32-S3 HID shell input on VT2 and CDC journal
output with the tablet acting as USB host. It opens an explicit local development
root shell; this profile is unsuitable as a general-purpose security default.
The existing bridge firmware, Uke USB/UFS DT support, UEFI handoff and measured
partition geometry still require independent acceptance. Construction starts
with `ukelinux.sh` in the workspace; see the [Core image guide](https://github.com/MCC45TR/uke-fedora-builder/blob/main/docs/IMAGES.md).

The [first local filesystem candidate](https://github.com/MCC45TR/uke-fedora-builder/blob/main/reports/CORE-FILESYSTEM-2026-10-05.json)
passed complete root/initramfs, EXT4/ESP and UKI byte-match checks. Its kernel
report retains missing enabled USB/UFS and static RAM; no image assets or tablet
boot acceptance are published.
