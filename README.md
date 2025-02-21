## 8812au ( 8812au.ko ) :rocket:

## Linux Driver for USB WiFi Adapters that are based on the RTL8812AU Chipset

- v5.13.6-23-g232107d9b.20210820 (Realtek) plus updates from the Linux community

> [!NOTE]
> Please read the file ["supported-device-IDs"](./supported-device-IDs) for information about how to confirm that this is the correct driver for your adapter.

> [!NOTE]
> As of Linux kernel 6.14, a Linux Standards comliant driver for the rtl8812au chipset is available and should make your adapter both plug and play and more feature filled.
>
> Additional information about this new driver along with ability to report bugs can be found at the following link:
>
> https://github.com/lwfinger/rtw88

> [!NOTE]
> The following links provide a lot of information about USB WiFi and are recommended reading:
>
> - [USB WiFi adapter information for Linux](https://github.com/morrownr/USB-WiFi/blob/main/home/USB_WiFi_Adapter_Information_for_Linux.md)
> - [USB WiFi adapters that are supported with Linux in-kernel drivers](https://github.com/morrownr/USB-WiFi/blob/main/home/USB_WiFi_Adapters_that_are_supported_with_Linux_in-kernel_drivers.md)

### Supported Features

- IEEE 802.11 b/g/n/ac WiFi compliant
- 802.1x, WPA2 AES for PSK and TLS (Radius)
- WPA3-SAE (Personal)
- IEEE 802.11b/g/n/ac Client mode
  * Supports wireless security for WPA2 AES PSK and WPA3-SAE
  * Supports site survey scan and manual connect
  * Supports TLS client
- TDLS support
- Power saving modes
- hostapd compatible
- AP mode DFS channel support
- Supported interface modes
  * IBSS (ad-hoc) (untested)
  * Managed (client)
  * AP (master) (see file 8812au.conf for hostapd configuration information)
  * P2P-client (Wi-Fi Direct)
  * P2P-GO (Wi-Fi Direct)
  * Concurrent (see docs folder for information)
- Log level control
- LED control
- Power saving control
- VHT control (allows 80 MHz channel width in AP mode)
- AP mode DFS channel control
- USB mode control

> [!NOTE]
> Monitor mode is not supported.
> Linux users that want good support for monitor mode in a dual band or tri-band adapter should seek out USB WiFi adapters based on the mt7610u, mt7612u or mt7921au chipsets.

### A FAQ is available in this repo with the name `FAQ.md`

- Please read the FAQ and this document before posting issues.

### Additional documentation is in the file `8812au.conf`

### Compatible CPU Architectures

- x86, i386, i686
- x86-64, amd64
- armv6l, armv7l (arm)
- aarch64 (arm64)
- riscv

> [!NOTE]
> Additional CPU architectures may work but are not tested.

### Compatible Kernels

- Kernels: 5.10 - 5.11 (Realtek)
- Kernels: 5.12 - 6.14 (community support)

> [!NOTE]
Note: Kernels earlier than 5.10 may work but are not tested.

### Tested Compilers

- gcc 12, 13 and 14

### Tested Linux Distributions

> [!NOTE]
> The information in this section depends largely on user reports which can be provided via PR or message in Issues.

- [Arch Linux](https://www.archlinux.org)
  - Kernels 5.4, 5.11 and 6.6

- [Armbian](https://www.armbian.com/)
   - Kernel 5.15 (Rock 4 SE (Rock 4b image with xfce))

- [Debian](https://www.debian.org/)
  - Kernels 5.10, 5.15, 6.1 and 6.6

- [Fedora](https://getfedora.org)
  - Fedora 38 (6.2.13-300)

- [Manjaro](https://manjaro.org)
  - Kernel 5.15

- [openSUSE](https://www.opensuse.org/) Tumbleweed (rolling)
  - Kernel 5.15

- [Raspberry Pi OS](https://www.raspberrypi.org) (2023-12-05)(ARM 32 bit and 64 bit)

- [Raspberry Pi Desktop](https://www.raspberrypi.org)
   - 2022-07-01
     - Kernel 5.10, x86_32

- [Ubuntu](https://www.ubuntu.com)
  - 22.04
    - Kernel 5.15
  - 24.04
    - Kernel 6.8
  - 24.10
    - Kernel 6.11
  - 

#### Red Hat Enterprise Linux (RHEL)

RHEL and distros based on RHEL are supported by Red Hat devs due to the way kernel patches are handled in Red Hat.
I support knowledgable RHEL developers if they want to merge the required support and keep it current.
I reserve the right to delete this support without notice if it causes any problems.

Current RHEL maintainer: none

#### Android

Android is supported in the driver according to Realtek.
I will support knowledgable Android developers if they want to merge and keep current the required support (most likely just instructions about how to compile and maybe a modification or two to the Makefile).

Current Android maintainer: none

#### OpenWRT

> [!WARNING]
> OpenWRT is _not_ supported with this driver.

OpenWRT provides drivers for USB WiFi adapters, modules and M.2 and PCIe cards.
OpenWRT provided drivers include support for the MT7925 (BE6500), MT7921au (AXE3000), MT7612u (AC1200), MT7610u (AC600) chipsets.
It is a challenge to use Realtek out-of-kernel drivers with OpenWRT so it is strongly advised to use the already supported chipsets.

### Compatible Devices

* ALFA AWUS036ACH
* ALFA AWUS036AC
* ALFA AWUS036EAC
* ASUS USB-AC56 Dual-Band AC1200 Adapter (H/W ver. A1)
* Belkin F9L1109
* Buffalo - WI-U3-866D
* Edimax EW-7822UAC
* Linksys WUSB6300 V1
* Netis WF2190
* Rosewill RNX-AC1200UBE
* Tenda U12
* TP-Link Archer T4U V1
* TRENDnet TEW-805UB

* Numerous additional adapters that are based on the supported chipset.

### Installation Information

It is recommended that you follow the installation instructions in the Installation Steps section.
Avoid installation by downloading the zip file if at all possible.
Support can only be provided, on a best effort basis, if the instructions in the Installation Steps section are followed.

> [!WARNING]
> Installing multiple out-of-kernel drivers for the same hardware usually does not end well.
> The `install-driver.sh` script has the capability to detect and remove most conflicting drivers but not all.
>
> If this driver does not work well after installation and you have previously installed a driver that you did not remove, it is suggested that you run the following command in an effort to determine if you need to take action to manually remove conflicting drivers:
> 
> ``` shell
> sudo dkms status
> ```

> [!IMPORTANT]
> If you decide to do a distro upgrade, which will likely install a new version of kernel such as 5.15 to 6.1, you need to update this driver with the newest available code and then reinstall it before performing the disto upgrade.
> See the section ["Upgrading the Driver"](#upgrading-the-driver) for the relevant instructions.

Internet access is required for initial installation.
There are numerous ways to enable temporary internet access depending on your hardware and situation.
[One method is to use tethering from a phone.](https://www.makeuseof.com/tag/how-to-tether-your-smartphone-in-linux).
Another method is to keep a [WiFi adapter that uses an in-kernel driver](https://github.com/morrownr/USB-WiFi/blob/main/home/USB_WiFi_Adapters_that_are_supported_with_Linux_in-kernel_drivers.md) in your toolkit.

You will need to use the terminal interface.
The quick way to open a terminal: Ctrl+Alt+T (hold down on the Ctrl and Alt keys then press the T key).

An alternative terminal is to use SSH (Secure Shell) from the same or from another computer, in which case you will be in a suitable terminal after logging in, but this step requires that an SSH daemon/server has already been configured.
(There are lots of SSH guides available, e.g., for the [Raspberry Pi](https://www.raspberrypi.com/documentation/computers/remote-access.html#setting-up-an-ssh-server) and for [Ubuntu](https://linuxconfig.org/ubuntu-20-04-ssh-server).
Do not forget [to secure the SSH server](https://www.howtogeek.com/443156/the-best-ways-to-secure-your-ssh-server/).)

You will need to have sufficient access rights to use `sudo` so that commands can be executed as the `root` user.
(If the command `sudo echo Yes` returns "Yes", with or without having to enter your password, you do have sufficient access rights.)

DKMS is used for the installation, if available.
DKMS is a system utility which will automatically recompile and reinstall this driver when a new kernel is installed.
DKMS is provided by and maintained by Dell.

It is recommended that you do not delete the driver directory after installation as the directory contains information and scripts that you may need in the future.

Secure Boot: see FAQ.

### Installation Steps

> [!NOTE]
> The installation instructions are for the novice user.
> Experienced users are welcome to alter the installation to meet their needs.
> Support will be provided, on a best effort basis, based on the steps below.
> Another way to word this paragraph is that if you do not follow the below steps for installation, you are your own tech support.

1. Open a terminal.
1. Update and upgrade system packages.

   The exact command will vary based on your Linux distribution.
   
   <details>
   
   <summary>Commands for some common distributions are provided below.</summary>
   
   - Debian-based distributions (including Ubuntu, Kali, Armbian, and Rasperry Pi OS):
   
     ``` shell
     sudo apt update && sudo apt upgrade
     ```
     
   - Arch-based distributions (e.g. Manjaro):

     ``` shell
     sudo pacman -Syu
     ```

   - Fedora-based distributions:

     ``` shell
     sudo dnf upgrade
     ```

   - openSUSE-based distributions:

     ``` shell
     sudo zypper update
     ```


   - Void Linux:

     ``` shell
     sudo xbps-install -Syu
     ```
     
   </details>

1. Reboot your operating system:

   ``` shell
   sudo reboot
   ```

1. Install the build dependencies.
 
   - Mandatory packages:
     - `gcc`
     - `make`
     - `bc`
     - `kernel-headers`
     - `build-essential`
     - `git`
   - Highly recommended packages:
     - `dkms`
     - `rfkill`
     - `iw`
     - `ip`
   - Mandatory packages if Secure Boot is active:
     - `openssl`
     - `sign-file`
     - `mokutil`
     
   The exact package names will vary based on your Linux distribution.

   > [!TIP]
   > If you are asked to choose a provider, make sure to choose the one that corresponds to your version of the linux kernel (for example, "linux510-headers" for Linux kernel version 5.10).
   > If you install the incorrect version, you'll have to uninstall it and install the correct version.
   
   <details>
   
   <summary>Commands for some common Linux distributions</summary>

   - Armbian (arm64):
   
      ``` shell
      sudo apt install -y build-essential
      ```
   
   - Raspberry Pi OS (arm/arm64):
   
     ``` shell
     sudo apt install -y raspberrypi-kernel-headers build-essential bc dkms git
     ```
   
   - Debian, Kali, and Raspberry Pi Desktop (x86):
   
     ``` shell
     sudo apt install -y linux-headers-$(uname -r) build-essential bc dkms git libelf-dev rfkill iw
     ```
   
     Additionally, if using kali-pi for RasPi4B/5B:
   
     ``` shell
     sudo apt install -y kalipi-kernel-headers build-essential bc dkms git
     ```
   
   - Ubuntu and Ubuntu-based distros:
   
     ``` shell
     sudo apt install -y build-essential dkms git iw
     ```
   
   - Fedora:
   
     ``` shell
     sudo dnf -y install git dkms kernel-devel
     ```

     If secure boot is active, also install `openssl`.
   
   - openSUSE:
   
     ``` shell
     sudo zypper install -t pattern devel_kernel dkms
     ```
   
   - Alpine:
   
     ``` shell
     sudo apk add linux-lts-dev make gcc
     ```
   
   - Void Linux:
   
     ``` shell
     sudo xbps-install linux-headers dkms git make
     ```
   
   - Arch and Manjaro (if using Manjaro for , see note)
   
     - If using RasPi4B/5B:
     
       ``` shell
       sudo pacman -S --noconfirm linux-rpi4-headers dkms git bc
       ```
   
     - For all other hardware:

       ``` shell
       sudo pacman -S --noconfirm linux-headers dkms git bc iw
       ```

1. Clone this repository.

   ``` shell
   git clone https://github.com/morrownr/8812au-20210820.git
   ```

1. Move to the newly created driver directory.

   ``` shell
   cd 8812au-20210820
   ```

1. Run the installation script.

   ``` shell
   ./install-driver.sh
   ```

> [!WARNING]
> The compilation may fail if the major version of gcc that is in use is not the same as the major version of gcc that was used to compile the kernel that is in use.
> 
> Example of bad situation:
> 
> ```
> gcc 12.1 (used to compile the kernel)
> gcc 10.3 (version of gcc in use)
> ```
> 
> Example of good situation:
> 
> ```
> gcc 12.2 (used to compile the kernel)
> gcc 12.1 (version of gcc in use)
> ```
> 
> To determine the values:
> 
> ``` shell
> cat /proc/version
> ```
> 
> ``` shell
> gcc --version
> ```
> 
> If you find your system in a bad situation, it is recommended that you install a version of gcc that matches the major version of gcc that was used to compile your kernel.
> Here is an example for Ubuntu:
> 
> ``` shell
> sudo apt install gcc-12
> ```

If your system is a low memory system, it is recommended that you terminate running apps so as to provide the maximum amount of RAM to the compilation process.

For automated builds (non-interactive), use `NoPrompt` as an option.

```
sudo ./install-driver.sh
```

or

```
sudo sh install-driver.sh
```

Note: If you elect to skip the reboot at the end of the installation
script, the driver may not load immediately and the driver options will
not be applied. Rebooting is strongly recommended.

Note: Fedora users that have secure boot turned on may need to run the
following to enroll the key:

```
sudo mokutil --import /var/lib/dkms/mok.pub
```

### Manual Installation Instructions

The installation script, `install-driver.sh`, automates the installation process.
If you want to or need to do a basic command line installation, though, this section lists the relevant steps.

> [!NOTE]
> If you use the Manual Installation Instructions, you will need to repeat the installation process each time a new kernel is installed in your distro.

1. `make clean`
1. `make -j$(nproc)`
1. If secure boot is off:
   1. `sudo make install`
   1. `sudo reboot`
1. If secure boot is on:

   Please read to the end of this section before coming back here to enter commands.

   1. `sudo make sign-install`

      You will be promted for a password, please remember the password as it will be used in some of the following steps.

   1. `sudo reboot`

   1. The MOK managerment screen will appear during boot with a message similar to the following:

      > Shim UEFI Key Management
      > Press any key...

    1. Select "Enroll key".

    1. Select "Continue".

    1. Select "Yes"

    1. When promted, enter the password you entered earlier.

       If you enter the wrong password, your computer will not be bootable.
       In this case:
       
       1. Use the BOOT menu from your BIOS to boot.
       1. `sudo mokutil --reset`
       1. Restart your computer.
       1. Use the BOOT menu from BIOS to boot.
       1. In the MOK managerment screen, select `reset MOK list`.
       1. Reboot.
       1. Rerun from the step `sudo make sign-install`.

### Manual Removal Instructions

To remove the driver if installed by the Manual Installation Instructions, run the following commands from your cloned copy of this repository.

1. `sudo make uninstall`
1. `sudo reboot`

If you use the manual installation instructions, or if dkms is not installed, you will need to repeat the process each time a new kernel is installed in your distro.

### Driver Options (`edit-options.sh`)

> [!TIP]
> In Linux, driver options are also called "module parameters".

A file called `8812au.conf` will be installed in `/etc/modprobe.d` by default if you use the installation script, [`install-driver.sh`](install-driver.sh).
If you are following the Manual Installation Instructions, you can use the [`edit-options.sh` script](edit-options.sh) to install and/or edit the file.

The installation script, [`install-driver.sh`](install-driver.sh), will prompt you to edit the options.

`8812au.conf` will be read and applied to the driver on each system boot.

To edit the driver options file, run the `edit-options.sh` script:

``` shell
sudo ./edit-options.sh
```

Documentation for Driver Options is included in the file [`8812au.conf`](8812au.conf).

### Upgrading the Driver

> [!TIP]
> Linux development is continuous, therefore work on this driver is continuous.

Upgrading the driver is advised in the following situations:

- every 2-3 months
- if a new or updated version of the driver needs to be installed
- if a distro version upgrade is going to be installed (i.e. going from kernel 5.10 to kernel 5.15)

To upgrade, perform the following steps:

1. Open a terminal (e.g. Ctrl+Alt+T).
1. Move to the driver directory, e.g. `cd ~/src/8812au-20210629`.
1. Pull updated code from this repo: `git pull`
1. Reinstall the driver: `sudo ./install-driver.sh`

   The `install-driver.sh` script will automatically remove the previously installed driver.

### Removal of the Driver (`remove-driver.sh`)

Removing the driver is advised in the following situations:

- if the driver is no longer needed

The following removes everything that has been installed, with the exception of the build dependency packages and the driver directory.
The driver directory can be deleted after running this script.

1. Open a terminal (e.g. Ctrl+Alt+T).
1. Move to the driver directory, e.g. `cd ~/src/8812au-20210629`.
1. Run the removal script: `sudo ./remove-driver.sh`

   For automated builds (non-interactive), use `NoPrompt` as an option.

### Recommended WiFi Router/ Access Point Settings

> [!NOTE]
> These recommendations apply when using your adapter in managed (client) mode, not AP mode.

These are general recommendations, some of which may not apply to your specific situation.

- Security

  Set WPA2-AES or WPA2/WPA3 mixed or WPA3.
  Do not set WPA2 mixed mode or WPA or TKIP.

- Channel width for 2.4 GHz

  Set 20 MHz fixed width.
  Do not use 40 MHz or 20/40 automatic.

- Channels for 2.4 GHz

  Set channel 1 or 6 or 11 depending on the congestion at your location.
  Do not set automatic channel selection.
  As time passes, if you notice poor performance, recheck congestion and set channel appropriately.
  The environment around you can and does change over time.

- Mode for 2.4 GHz

  For best performance, set "N only" if you no longer use B or G capable devices.

- Network names

  Do not set the 2.4 GHz Network and the 5 GHz Network to the same name.

  Unfortunately many routers come with both networks set to the same name.
  You need to be able to control which network that is in use so changing the name of one of the networks is recommended.
  Since many IoT devices use the 2.4 GHz network, it may be better to change the name of the 5 GHz network.

- Channels for 5 GHz

  Not all devices are capable of using DFS channels (I'm looking at you Roku).
  It may be necessary to set a fixed channel in the range of 36 to 48 or 149 to 165 in order for all of your devices to work on 5 GHz. (For US, other countries may vary.)

- Best location for the WiFi router/access point

  Near center of apartment or house, at least a couple of feet away from walls, in an elevated location.
  You may have to test to find the best location is in your environment.

- Check congestion

  There are apps available for smart phones that allow you to get an idea of the congestion levels on WiFi channels.
  The apps generally go by the name of `WiFi Analyzer` or something similar.

After making and saving changes, reboot the router.

### Recommendations regarding USB

- Moving your USB WiFi adapter to a different USB port has been known to fix a variety of problems.

- If connecting your USB WiFi adapter to a desktop computer, use the USB ports on the rear of the computer if you encounter any problems.
  Why?
  The ports on the rear are directly connected to the motherboard which will reduce problems with interference and disconnection.
  An extension cable can be helpful to position the adapter for best reception.

- If your USB WiFi adapter is USB 3 capable and you want it to operate in USB3 mode, plug it into a USB 3 port.

- Avoid USB 3.1 Gen 2 ports if possible as most currently available adapters have been tested with USB 3.1 Gen 1 (aka USB 3) and not with USB 3.1 Gen 2.

- If you use an extension cable and your adapter is USB 3 capable, the cable needs to be USB 3 capable (if not, you will be limited to USB 2 speeds).

- Extension cables can be problematic.
  A way to check if the extension cable is the problem is to plug the adapter temporarily into a USB port on the computer.

- Some USB WiFi adapters require considerable electrical current and push the capabilities of the power available via USB port.
  One example is adapters that use the Realtek 8814au chipset.
  Using a powered multiport USB extension can be a good idea in cases like this.

-----

To Contribute:

- Fork this repository.
- Make your edits.
- TEST THEM!
- Create a pull request.

-----

#### [Go to Main Menu](https://github.com/morrownr/USB-WiFi)

-----
