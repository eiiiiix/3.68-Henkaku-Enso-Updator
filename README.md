# 3.65 HENkaku Ensō Updater

## This does not allow you to hack your console that is on a firmware past 3.68. You need to be on firmare 3.65 in order to use this software.

Custom Firmware 3.68 HENkaku Ensō is a port of [henkaku](https://github.com/henkaku) to the latest possible firmware that does still have the bootloader vulnerability.

## Pros and cons
### Pros
- You will be able to access the PSN store, activate your device and download your purchased games again (only as long as Sony doesn't decide to release a new update that prevents you from doing that).
- You will be able to play all games that were released for firmwares 3.61-3.68.
### Cons
- You will not be able to downgrade back to 3.65 if you find that this custom firmware doesn't suit you.
- You can lose the ability to run homebrews, if you modify the OS and end up in a semi-brick where you are forced to reinstall the firmware. This should however not happen to a regular user, but I'd rather not install applications that modify read-only partitions like `os0:` or `vs0:`.
- Some applications may not work on the new firmware and need to be ported.

## Instructions
1) If you are on a firmware below 3.65, update to 3.65 and install [henkaku](https://henkaku.xyz/).
2) Update [VitaShell](https://github.com/TheOfficialFloW/VitaShell/releases) to v1.93 or later (if you get an error when trying to install the vpk, simply rename the vpk to zip and manually copy the `eboot.bin` file to `ux0:app/VITASHELL/eboot.bin`).
3) Make a CMA backup of VitaShell. **This is very important, since if you lose VitaShell this is the way you restore it**.
4) Download and compile the source code
5) Install `updater.vpk` using `VitaShell` and put the `PSP2UPDAT.PUP` file at `ux0:app/UPDATE365/PSP2UPDAT.PUP`.
6) If you have been already been using 3.65 HENkaku (Enso), uninstall all plugins and uninstall the enso patch. It is recommended to first unlink the Memory Card in `HENkaku Settings` just before you uninstall enso, so that your Memory Card won't be restricted afterwards due to the spoofed version at `ux0:id.dat` when it reboots into offical firmware. Uninstalling all plugins and the enso patch is extremely important, as they can interfere with the update process if enabled (the updater will notice you in case you have not uninstalled them correctly).
7) Reboot your device, start HENkaku and directly launch the updater, without launching anything else before like VitaShell or Adrenaline (since they start kernel modules). Also make sure that your battery is at least at 50%.
8) Follow the instructions on screen and enjoy the update process.
9) When the updater finishes flashing the new firmware, custom modules will be written to `vs0:tai` and the bootloader hack injected to the eMMC. You should now be on 3.68 HENkaku Ensō.

## FAQ
- "Are Adrenaline, DownloadEnabler, NoNpDrm and SD2VITA compatible on 3.68?" - Yes they have all been updated and are available under my repositories.
- "Is it risky to perform this update?" - All my betatesters have successfully updated and have no issues so far. The updater has been designed carefully, so you don't need to worry.
- "Will I lose the hack if I format my Memory Card or restore the systems settings?" - No, you can nearly do everything with your device and you will not lose HENkaku. You must just NOT reinstall the 3.68 PUP.
- "I have installed a bad plugin and now my device doesn't boot anymore" - Try to enter the `Safe Mode` and choose `2. Rebuild Database`. This will allow you to boot the device with plugins disabled and fresh `config.txt` files.
- "I have lost molecularShell/VitaShell!" - You proceeded through the updater without carefully reading it. Congratulations! You can simply restore it by using CMA and [psvimgtools](https://github.com/yifanlu/psvimgtools), but since you didn't made a backup as it was CLEARLY stated in the updater, it's your own fault and you will now have to figure out yourself how to solve this problem.
- "I forgot to unlink the Memory Card before uninstalling enso now I can't use it!" - simply start HENkaku again through the browser, open settings app and then choose HENkaku Settings.
- "I have only got a SD2VITA but no Memory Card, how can I update?" - If you are using a PS Vita Slim or PSTV, you can just use the Internal Storage to update, otherwise you can't. When you use SD2VITA you have to use a plugin for that. But plugins are dangerous since they can interfere with the update process which can lead to a brick in the worst case. An other reason is that I want to prevent this scenario: Imagine an user forgets to update the sd2vita plugin and updates to 3.68, then realizes that the driver his unsupported. He will then be forced to buy a Memory Card in order to do anything with the new custom firmware.

## Donation
If you like my work and want to support future projects, you can make a small donation with [paypal](https://www.paypal.me/PSVitaTheFloW/20) or bitcoin `361jRJtjppd2iyaAhBGjf9GUCWnunxtZ49`. Thank you!

## Compiling
Compile `enso`, `henkaku` and [taihen](https://github.com/TheOfficialFloW/taiHEN), then put the binaries `fat.bin`, `henkaku.suprx`, `henkaku.skprx` and `taihen.skprx` at `installer/res`. Then you can compile the installer. It is however very dangerous to do this by yourself if you don't know what you're doing. One mistake means a bricked device. If you want to only compile the installer, then simply open `updater.vpk` as zip file and use the three binaries from there.

## Credits
- [molecule](https://twitter.com/TeamMolecule) for their original work.
- [Mathieulh](https://twitter.com/Mathieulh) for providing his devkit.
- [Freakler](https://twitter.com/freakler94) for his LiveArea design.
