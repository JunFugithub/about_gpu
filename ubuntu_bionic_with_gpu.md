## Gpu 3rd library incompatibale

except debian there always are issues while installing linux-like OS on a laptop with *individual* GPU (I haven't exprimented on some other release yet, but someone else from internet told me like that). The 3rd library is called **nouveau**, it directly results in being stuck in installation part. The solution there is to press __'e'__ while installation menu occurs, then u r getting into the _grub menu_. Afterwards, we r going to modify the line with `quiet splash` and put `nomodeset` in the end of that line to replace `---` maybe.

```bash
quiet splash nomodeset
```

By means of upper-mentioned modification, the installation is going smoothly. However, it gets stuck in logging as well. Reboot and log in with grub menu, too. Then, we r going to modify __/boot/grub/grub.cfg__ with doing the same thing as the upper way in line with _quiet splash_.

Even though we r able to log in normally, but you must notice the resolution of screen is kinda wired. That's because we disable the use of **nouveau** which means it should be displayed irregularly. In order to fix it, we need to do something as following:

- disable __'secure boot'__
- add `blacklist nouveau` up to _'/etc/modprobe.d/blacklist.conf'_ and refresh with `sudo update-initramfs -u`.
- reboot and stop service `lightdm`
- download the driver mannually from official nvidia site or `$ ubuntu-drivers devices` & `$ sudo ubuntu-drivers autoinstall` 

And now it might work appropriately

## TODO
nvidia-smi still can't work properly with prompt `"NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running"`

[ref1](https://blog.csdn.net/kilotwo/article/details/79258107)

[ref2](https://www.jianshu.com/p/6482dca83bd4)
