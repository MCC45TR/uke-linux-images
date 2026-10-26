# Fedora Rawhide KDE testing image — 26 October 2026

Uke AArch64, original Fedora KDE Plasma, singleboot EXT4 on `userdata`, with
matched Linux `7.3.0-16` boot, device trees and modules. Packages come from the
signed `mcc45tr/uke-linux-test` repository. The initial filesystem is 16 GiB.

| Item | Source / record |
|---|---|
| Image recipe | [b0fd238](https://github.com/MCC45TR/uke-fedora-builder/tree/b0fd2380b07dbaaf37403c057b74796faf8f5ed3) |
| Kernel source | [c5e9641](https://github.com/MCC45TR/senemos-uke-kernel-mainline/tree/c5e9641ba311d536357d3a135750f44502352ae1) |
| Control packaging | [c4fa10e](https://github.com/MCC45TR/uke-linux-hardware-support/tree/c4fa10ec9256cd0fb65a27fd1430406139966046), signed 1.15.0-2, [COPR 11209527](https://copr.fedorainfracloud.org/coprs/build/11209527/) |
| Downloads and installation | [Main project prerelease](https://github.com/MCC45TR/uke-linux/releases/tag/prebuild-fedora-kde-singleboot-ext4-20261026-k7.3.0-16-testing) |
| Asset checksums | [SHA256SUMS](SHA256SUMS) |
| Image provenance and validation | [manifest.json](manifest.json) |
| Installed packages | [installed-rpms.tsv](installed-rpms.tsv) |

The checked-in workspace `ukelinux.sh` is invoked with:

```sh
./ukelinux.sh --build image --mode singleboot --filesystem ext4 \
  --desktop kde --channel testing --defer-touch-reference
```

Use the [frozen release guide](https://github.com/MCC45TR/uke-fedora-builder/blob/b0fd2380b07dbaaf37403c057b74796faf8f5ed3/docs/PUBLIC-BUILD.md)
for this recipe. The default builder branch has its own source-build workflow.
The recipe selects 16 workers on the recorded Fedora x86_64 host, AArch64
package scriptlets under QEMU, and a separate libguestfs TCG appliance for
filesystem population/readback. A second clean build remains untested.

This generic image excludes the device-local touch reference. Provision the
**target tablet's own accepted 5,432-byte reference** at
`/var/lib/uke-touch/reference.bin`, `root:root`, mode `0600`, before touchscreen
account setup. The service remains inactive without it. USB-only first setup is
not qualified. There is no default user/password; SSH is disabled. Original
KDE Connect, its daemon/autostart files and desktop firewall policy are included.

OEM firmware comes from the signed public `uke-firmware` package and retains
its supplied notices. Firmware licensing is separate from project source
licenses; the manifest retains the redistribution-review flag.

Host output checks are recorded separately from device results. These exact
files have not been flashed or booted on a tablet. First setup, filesystem
growth, updates, recovery and hardware lifecycle remain open. Results from the
POCO Pad X1 development installation do not qualify this exported filesystem.
Xiaomi Pad 7 and other memory/storage variants are untested.

**Writing `userdata` destroys Android data.** Preserve stock early firmware,
`boot_a`, compatible slot-B firmware and a verified recovery route. Read the
release's capacity checks and recovery instructions before installation.
After the first Fedora boot, run `sudo dnf update --refresh`; automatic
kernel/slot activation remains disabled.
