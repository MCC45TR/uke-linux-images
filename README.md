# Uke Linux images

Release records for experimental Fedora AArch64 images for Xiaomi Pad 7 and POCO Pad X1 (`uke`, SM7675).

**Availability and status checked 26 October 2026.**

[Current project status](https://github.com/MCC45TR/uke-linux) · [Main releases](https://github.com/MCC45TR/uke-linux/releases) · [Source build guide](https://github.com/MCC45TR/uke-fedora-builder/blob/main/docs/PUBLIC-BUILD.md)

## Available releases

| Release | Availability | Scope |
|---|---|---|
| [Fedora Rawhide Alpha 1](https://github.com/MCC45TR/uke-linux/releases/tag/fedora-rawhide-alpha-1), 15 October | Three attached boot/root image files | Linux 7.2.9 revision 1.39. Historical experimental alpha; exact exports have not completed tablet validation. |
| [KDE EXT4 singleboot testing](https://github.com/MCC45TR/uke-linux/releases/tag/prebuild-fedora-kde-singleboot-ext4-20261024-k7.2.12-22-testing), 24 October | Release notes; no attached image assets at the time of this update | Original Fedora KDE, signed 7.2.12-22 package composition and host image checks. Earlier direct asset links are unavailable. |
| [Older image records](https://github.com/MCC45TR/uke-linux-images/releases) | Historical releases and their original requirements | Read each exact artifact's checksums and installation scope. |

No new image was built, uploaded or qualified by this documentation update. Do not treat current Linux 7.3 development results as validation of an older exported root image.

## Development installation

POCO Pad X1 runs Fedora Rawhide and original KDE in a separate development installation. The latest normal boot record is Linux 7.3.0-15. Display, normal touch, Wi-Fi, selected Bluetooth and sensor functions have recorded results, with unresolved charging, sleep, display lifecycle, audio, camera and video work.

See the [complete hardware table](https://github.com/MCC45TR/uke-linux#hardware-support) for dated function-level limits. Xiaomi Pad 7 and other variants have not received equivalent physical validation.

## Build and installation

Use the checked-in workspace workflow:

```sh
git clone --recurse-submodules https://github.com/MCC45TR/uke-linux.git
cd uke-linux
./ukelinux.sh
```

The [public guide](https://github.com/MCC45TR/uke-fedora-builder/blob/main/docs/PUBLIC-BUILD.md) defines source selection, prerequisite confirmation, output checks and manual terminal installation. Keep exact boot/root/module identities matched and preserve stock early firmware plus a verified recovery route.

Writing Android `userdata` destroys applications, files and encryption metadata. A userdata-root singleboot image is not a data-preserving dual-boot route. Device-local touch references and calibration are not portable to another tablet.

After the first Fedora boot, run `sudo dnf update --refresh`. Original KDE packages retain their distribution-provided helpers; project recovery, initramfs and installers do not add Python.

## Sources and reporting

| Resource | Location |
|---|---|
| Public status and releases | [uke-linux](https://github.com/MCC45TR/uke-linux) |
| Image recipes | [uke-fedora-builder](https://github.com/MCC45TR/uke-fedora-builder) |
| Kernel source and packages | [senemos-uke-kernel-mainline](https://github.com/MCC45TR/senemos-uke-kernel-mainline) |
| Platform packages | [uke-linux-hardware-support](https://github.com/MCC45TR/uke-linux-hardware-support) |
| Bug reports | [Reporting guide](https://github.com/MCC45TR/uke-linux/blob/main/CONTRIBUTING.md) |

Each delivery needs exact source/package versions, checksums, kernel/DTB identity, filesystem size, device/firmware scope and rollback requirements. Keep host, VM and tablet results separate. Public reports exclude credentials, unit identifiers, calibration and private logs.

This is an independent community project. Documentation follows the [project report style](CONTRIBUTING.md).
