<div align="center">
  <img src="https://nexalinux.xyz/nexa2.png">
  <h1>Nexa Linux - ISO builder</h1>
  <p>Penguins' Eggs was hard to maintain, so here we are, with a fork of [Rhino Linux's ISO builder](http://github.com/rhino-linux/os/) with Nexa Linux changes.</p>
</div>

> [!CAUTION]
> This builder is W.I.P. Do not use!

To use this ISO builder, you must prepare your converted system with these commands:

- `sudo apt-get update && sudo apt-get install --reinstall debootstrap -y`
- `sudo mv /usr/share/debootstrap/functions functions`
- `sudo patch -i 0002-remove-WRONGSUITE-error.patch`
- `sudo mv functions /usr/share/debootstrap/functions`
- `sudo ln -sfn /usr/share/debootstrap/scripts/gutsy /usr/share/debootstrap/scripts/lunar`
- `sudo dpkg -i debs/live-build_*_all.deb`
- `sudo cp binary_grub-efi /usr/lib/live/build/binary_grub-efi`
- `sudo chmod -R +x build.sh etc/auto/config etc/terraform.conf etc/`

Then, to build the ISO: 

`sudo ./build.sh etc/terraform.conf`

The resulting ISO, if successful, will be located in builds/`$ARCH`. **Keep in mind, we do not support ARM64 nor 32-bit builds!**

This build system creates the images using `lb`/live-build with debootstrap to create images with configuration in `etc` folder.

# Credits:
- [Rhino Linux](https://github.com/rhino-linux/) for making the [ISO builder](http://github.com/rhino-linux/os/) (which this repo is a fork of).
