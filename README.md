# Linux Surface

Linux running on the Microsoft Surface devices.
Follow the instructions below to install the latest kernel and config files.

### Supported Devices

* Surface Book
* Surface Book 2
* Surface Go
* Surface Laptop
* Surface Laptop 2
* Surface Laptop 3
* Surface Pro 3
* Surface Pro 4
* Surface Pro 2017
* Surface Pro 6
* Surface Pro 7
* Surface Studio

### Features / What's Working

See the [feature matrix](https://github.com/linux-surface/linux-surface/wiki/Supported-Devices-and-Features#feature-matrix) for more information about each device.

### Disclaimer

* For the most part, things are tested on a Surface Book 2.
  While most things are reportedly fully working on other devices, your mileage may vary.
  Please look at the issues list for possible exceptions. 

## Installation and Setup

For a more detailed installation and setup guide, please refer to the corresponding [Wiki page][wiki-setup].
There, you may also find device-specific caveats.
A short overview of the process is provided below.

Releases are provided for both Debian and Arch Linux based distributions, but if you're running Arch, you may want to consider looking at [this][arch-linux-surface] project instead, or [here][fedora-linux-surface] if you're running Fedora.
These releases can be found here: https://github.com/linux-surface/linux-surface/releases.

You may also want to consider setting up one of the [package repositories][wiki-repos] to obtain automatic updates.
After the installation, you should have a look at the [post-installation notes][wiki-setup-post], specifically you may want to set up [secure-boot][wiki-secure-boot] and install the proprietary firmware package (usually named `linux-firmware`) if you have not done so already.

1. Before you can actually start, you will need to install some required packages.
   On Debian based distributions, you can do this by simply running
   ```
   sudo apt install git
   ```

2. **Clone this repository.**
   To save some time, you can use the `--depth 1` flag.
   ```
   git clone --depth 1 https://github.com/linux-surface/linux-surface.git
   ```
   If you want to update this git repository later on, e.g. for re-running the `setup.sh` script, you can simply run `git pull` inside the repository.

3. Next, change into the `linux-surface` directory (`cd linux-surface`) and run the setup script via
   ```
   sudo ./setup.sh
   ```
   Follow the instructions and make your choices.

4. **Download and install the required packages.**
   You can use one of the package repositories to install the kernel and libwacom package.

   Alternatively, you can also install them manually via (for Debian) after
   downloading these files from the [releases][releases] section of this repo.
   ```
   sudo dpkg -i linux-headers-[VERSION].deb linux-image-[VERSION].deb linux-libc-dev-[VERSION].deb
   ```

5. Finally, you will need to re-boot your system and boot into the linux-surface kernel.
   Please make sure that you actually boot in the right kernel via `uname -a` before opening any issues.
   This should give you a version string containing `surface`.
   If not, you may need to configure your bootloader.
   For this, please refer to the instructions provided by your bootloader and/or distribution.


If you want to compile the kernel yourself (e.g. if your distribution is not supported), please have a look at the [wiki][wiki-compiling].


## Additional Information

### Notes

* If you are getting stuck at boot when loading the ramdisk, you need to install the Processor Microcode Firmware for Intel CPUs (usually found under Additional Drivers in Software and Updates).
* Do not install TLP! It can cause slowdowns, laggy performance, and occasional hangs! You have been warned.
* If you want to use hibernate instead of suspend, you need to create a swap partition or file, please follow your distribution's instructions (or [here][hibernate-setup]).

### Support

If you have questions or need support, please use our [Gitter Community][gitter]!
For development related questions and discussions, please consider joining our IRC channel on freenode (`freenode/##linux-surface`) or the [equivalent Matrix bridge](https://matrix.to/#/#freenode_##linux-surface:matrix.org).

[wiki-setup]: https://github.com/linux-surface/linux-surface/wiki/Installation-and-Setup
[wiki-setup-post]: https://github.com/linux-surface/linux-surface/wiki/Installation-and-Setup#post-installation
[wiki-repos]: https://github.com/linux-surface/linux-surface/wiki/Package-Repositories
[wiki-secure-boot]: https://github.com/linux-surface/linux-surface/wiki/Secure-Boot
[wiki-compiling]: https://github.com/linux-surface/linux-surface/wiki/Installation-and-Setup#compiling-the-kernel-from-source

[arch-linux-surface]: https://github.com/dmhacker/arch-linux-surface
[fedora-linux-surface]: https://github.com/StollD/fedora-linux-surface/

[gitter]: https://gitter.im/linux-surface
[hibernate-setup]: https://fitzcarraldoblog.wordpress.com/2018/07/14/configuring-lubuntu-18-04-to-enable-hibernation-using-a-swap-file
[releases]: https://github.com/linux-surface/linux-surface/releases

[linux-surface-kernel]: https://github.com/linux-surface/kernel/
