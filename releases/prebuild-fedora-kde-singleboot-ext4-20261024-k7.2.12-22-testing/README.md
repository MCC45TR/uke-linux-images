# Fedora KDE singleboot EXT4 testing image — 24 October 2026

Target: Uke, Fedora Rawhide AArch64, original Fedora KDE and signed testing kernel `7.2.12-22.fc46.aarch64`. The build request used 16 workers. Kernel RPMs were retrieved from `mcc45tr/uke-linux-test`, not compiled locally.

The release assets are `boot.img` and `system.img.zst`. Decompression produces the Android sparse `system.img`, which targets `userdata`; its initial expanded EXT4 size is 16 GiB. The matching 96 MiB boot image targets `boot_b`. Checksums and manual installation instructions are in the release description.

These records provide the image manifest, full installed RPM/source-RPM inventory, signature-key identity and signed kernel input hashes. The two source patches reconstruct the recorded builder and kernel CLI trees from the public base commits listed in `source-and-package-manifest.json`.

Host filesystem content, ownership, modes, capabilities, ACLs, SELinux, original-Fedora helper and language audits passed. Both the project sparse decoder and AOSP `simg2img` passed full byte comparisons. Standard stages were resumed after host-tooling corrections; an independent clean repeat build is untested.

This exact image has no tablet installation, first-setup, boot, runtime, filesystem-growth or rollback acceptance. It contains a device-local touch reference and is device-specific. The OEM firmware package's file-level redistribution review remains incomplete. These records do not establish generic-device suitability or firmware redistribution clearance.
