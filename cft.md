# Call for testing: KDE installation script

The purpose of this script is to install and configure a graphical environment that starts automatically after reboot.
At the moment, development is focused on: GPU, Xorg, KDE Plasma, and SDDM. Additional options may be added in the future.

**This script is still experimental, participate only if you are familiar with configuring and using FreeBSD.**

## Testing

The script is intended to be integrated into bsdinstall, but it is currently in the testing phase and must be run after installation. The script can be tested immediately after an installation or on an already installed system.

### Testing after installation (Live CD)

1. Install FreeBSD. You may choose pkgbase (including minimal installation) or distribution extraction.
2. On the final screen, select “LIVE CD”.
3. Run the following commands:
```
# fetch https://gitlab.com/alfix/kde-installer-dialogs/-/raw/main/desktop
# ./desktop
```

### Testing on an installed system

Run the following commands:
```
# fetch https://gitlab.com/alfix/kde-installer-dialogs/-/raw/# main/desktop
./desktop
```

### Testing warning

 - If the script is executed multiple times, it duplicates configuration entries in `/etc/rc.conf` and `/boot/loader.conf`.
 - The script currently does not check whether options are already enabled.

After installation, please manually verify both configuration files. This limitation will be addressed when the script is updated for integration with bsdinstall. More details are available [here](https://gitlab.com/alfix/kde-installer-dialogs/-/issues/20#note_3011254558).

## Reporting

I am particularly interested in NVIDIA hardware testing, as I do not own a recent laptop with this hardware.
[My laptop](https://wiki.freebsd.org/Laptops/Acer_Aspire_5742G) with NVIDIA Optimus dates back to 2011.

### Successful test

If your test is successful, please add an entry to the table below by submitting a
[Pull Request on GitHub](https://github.com/alfonsosiciliano/kde-installer-dialogs/pulls)
or a
[Merge Request on GitLab](https://gitlab.com/alfix/kde-installer-dialogs/-/merge_requests).

 - FreeBSD Version: output of `uname -rK` and real hardware or virtual machine.
 - GPU: `pciconf -lv | grep -A 4 vga` and `fwget -nq | grep gpu`
 - Driver: selected GPU item in the radiolist dialog (AMD, Intel, nvidia-drm-kmod, nvidia-driver-XYZ, etc.)  
 - Notes: optional.

| FreeBSD Version | GPU | Driver | Notes |
| --------------- | --- | ------ | ----- |
| 16.0-CURRENT 1600009 | Intel HD Graphics 620 | Intel | Lenovo Yoga 11e |
|                 |     |        |       |
|                 |     |        |       |
|                 |     |        |       |
|                 |     |        |       |
|                 |     |        |       |
|                 |     |        |       |
|                 |     |        |       |
|                 |     |        |       |

### Failed test

If the test fails, please report the issue with a detailed description.
You can submit a new issue on either
[GitLab](https://gitlab.com/alfix/kde-installer-dialogs/-/issues) or
[GitHub](https://github.com/alfonsosiciliano/kde-installer-dialogs/issues).

## Thank you in advance for your report!

