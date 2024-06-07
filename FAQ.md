## FAQ

### Secure Boot Information

> The driver installation script completed successfully and the driver is installed but does not seem to be working.
> What is wrong?

This question often comes up after installing the driver to a system that has Secure Boot on.
To test if there is a Secure Boot related problem, turn secure boot off in the system BIOS and reboot.
If the driver works as expected after reboot, then the problem is likely related to Secure Boot.

> What will increase my chances of having a sucessessful installation on a system that has Secure Boot on?

First and foremost, make sure Secure Boot is on when you initially install your Linux distro.
If your Linux distro was installed with Secure Boot off, the easiest solution is likely to do a clean reinstallation with Secure Boot on.

Ubuntu is used as the example but other distros should be similar to one degree or another.
During the installation there may be a box on one of installation pages that will appear if the installation program detects that Secure Boot is on.
You will need to check the appropriate box and supply a password.
You can use the same password that you use for the system if you wish.
After the installation and reboot completes, the first screen you should see is the mokutil screen.
Mokutil will guide you through the process of setting up your system to support Secure Boot.
If you are unsure what to do, I recommend you seek guidance from your distro documentation or user forums.
Having Secure Boot properly set up in your installation is very important.

Resources:

- The `install-driver.sh` script currently supports Secure Boot if `dkms` is installed.
- Here is a link to the `dkms` website: <https://github.com/dell/dkms>
- Here is a link regarding Debian and Secure Boot: <https://wiki.debian.org/SecureBoot>
- If you are using a basic command line (non-dkms) installation, see the ["Manual Installation Instruction" section in this repo's README](./README.md#manual-installation-instructions).
  It provides secure boot instructions for a manual installation.

### WPA3

> Is WPA3 supported?

WPA3-SAE is supported.
It works well on most modern Linux distros.
Generally the reason for WPA3 not working on Linux distros is that the distro has old versions of components required for WPA3 support.
This includes, but is not limited to, utilities such as wpa\_supplicant or Network Manager.
Your options are to upgrade to a more modern distro such as those released after mid-2022 or determine what the problem is and figure out how to fix it.
Fixes could include compiling and installing new versions of wpa\_supplicant and/or Network Manager.

### Multiple USB Adapters

> I bought two usb wifi adapters based on this chipset and am planning to use both in the same computer.
> How do I set that up?

Realtek drivers do not support more than one adapter with the same chipset in the same computer.
You can have multiple Realtek based adapters in the same computer as long as the adapters are based on different chipsets.

### Why Mediatek?

> Why do you recommend Mediatek based adapters when you maintain this repo for a Realtek driver?

When Realtek makes the decision to move to exclusively using a modern standards compliant Linux driver model, I will consider changing this recommendation.
Until that happens, I will continue to recommend Linux users buy new adapters that use Mediatek chipsets.
However...

Many new and existing Linux users already have adapters based on Realtek chipsets so this repo will be supported as long as it is needed and I am able to maintain it.

> [!TIP]
> More information about recommended adapters an be found at <https://github.com/morrownr/USB-WiFi>.

### How Can I Contribute?

> Will you put volunteers to work?

Yes. Post a message in `Issues` if interested.

### Virtual Machines

> I am having problems with my adapter and I use Virtualbox or another VM.

Running under VMs is not supported.
It can work but you are your own techical support.
There are guides available on the internet and it is recommended that you seek support with the provider of the VM.

There are alternatives to using VMs.
For example: Almost all Linux distros support installing in a Dualboot or Multiboot configuration.
This will eliminate the many problems associated with using USB WiFi adapters in a VM.

### Raspberry Pi 4B/400

> When running `sudo sh install-driver.sh` on my RasPi 4B or 400, I see the following:
>
>> Your kernel header files aren't properly installed.
>> Please consult your distro documentation or user support forums.
>> Once the header files are properly installed, please run...

The Pi 4/400 firmware now prefers the 64-bit kernel if one exists so even if you installed the 32 bit version of the RasPiOS, you may now have the 64 bit kernel active.

To fix, add the following to `/boot/config.txt` and reboot:

``` text
arm_64bit=0
```

Reference: <https://forums.raspberrypi.com/viewtopic.php?p=2091532&hilit=Tp+link#p2091532>

> [!NOTE]
> If your RasPi is capable of using a 64 bit version of the RasPiOS, it is recommended that you use a 64 bit version of the RasPiOS as this will eliminate this problem.

Note to RasPiOS devs:
We really really wish you would consider the consequences of the changes you make.
Thank you.
