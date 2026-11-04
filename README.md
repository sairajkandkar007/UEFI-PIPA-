# Project Silicium UEFI for ARM64-Based Devices

<!-- ![Banner](https://github.com/Project-Silicium/Mu-Silicium/blob/main/Resources/Pictures/Banner.png) -->

## Description

This Project focuses on Making ARM-Based Devices Boot Operating Systems like Windows or Linux using Custom UEFI Firmware.

## Xiaomi Pad 6 (pipa): Secure Boot build

A dedicated GitHub Actions workflow builds the Xiaomi Pad 6 UEFI image without requiring pipa to be marked Active in `Status.md`.

1. Open **Actions → Build Xiaomi Pad 6 Secure Boot UEFI**.
2. Select **Run workflow**.
3. Choose `RELEASE` for normal use (or `DEBUG` for diagnostics).
4. Keep **Enable Secure Boot** checked.
5. Download the `pipa-uefi-…-secureboot` artifact after the workflow succeeds. It contains `Mu-pipa.img`.

The workflow builds the existing pipa platform package (`Platforms/Xiaomi/pipaPkg`) with the build system's `-s/--enable-secureboot` option. The Secure Boot configuration currently uses the Project Silicium key material and policy already present in this source tree; it is **not a personal-key build**. Do not describe it as Xiaomi/OEM Secure Boot, and do not assume it will boot binaries that are not trusted by the enrolled keys.

**Device safety:** this workflow only compiles and uploads an image. It does not flash the tablet, unlock/lock the bootloader, or change Android partitions. Keep the bootloader unlocked while testing custom firmware, retain a known-good recovery/stock restore path, and verify the image and its trust chain before any device-side installation. Enabling UEFI Secure Boot does not itself re-enable Android Verified Boot or relock Xiaomi's bootloader.

## Resources

- [Status](Status.md)
- [Building](Building.md)
- [Guides](https://github.com/Project-Silicium/Guides/blob/main/README.md)
- [Discord Server](https://discord.gg/Dx2QgMx7Sv)

## Frequently asked Questions

### **Is my Device Supported in this Project?**
- To Check if your Device is Supported, Take a Look at the Status Page Referenced in the Section Above.

### **What do I do if my Device isn't Supported in this Project?**
- We made some Guides that Explain How to Port your Device that are Referenced in the Section Above.

## Credits

[Microsoft](https://github.com/microsoft/) for their [Project Mu](https://microsoft.github.io/mu/) which Powers this Project. <br>
[WOA-Project](https://github.com/WOA-Project/) for their [mu_andromeda_platforms](https://github.com/WOA-Project/mu_andromeda_platforms/) which is used as Base for this Project. <br>
[Project Aloha](https://github.com/Project-Aloha/) for their [mu_aloha_platforms](https://github.com/Project-Aloha/mu_aloha_platforms/) which is used as Reference for some SoCs. <br>
[Open Surface RT](https://openrt.gitbook.io/open-surfacert/) for their Help on Tegra Related Stuff.

[sonic011gamer](https://github.com/sonic011gamer/) and [halal-beef](https://github.com/halal-beef/) for their Amazing Work on Exynos Related Stuff.

## License

All code except drivers in `GPLDrivers` & `GPLApplications` & `GPLLibrary` directories are licensed under BSD-2-Clause. <br />
GPL Drivers are licensed under `GPLv2` or later license.
