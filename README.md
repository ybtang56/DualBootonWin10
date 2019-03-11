# DualBootonWin10
Instructions to install Ubuntu on Win10

## Test Enviroment
  * Clean Dell 15' PRECISION
  * Default Windows 10 

## Operations
  * Prepare the Ubuntu USB drive via [**Etcher**](https://www.balena.io/etcher/) or [**Universal USB Installer**](https://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
  * Shrink a disk volumn for the Ubuntu. **Shrink** no more **Creation** actions
  * **F2 into BIOS Setting - IMPORTANT!!!**
    * System Configuration -> SATA Operation -> AHCI
    * Secure Boot -> Secure Boot Enable -> Disable
    * General -> Advanced Boot Options -> Enable Legacy Option ROMs
    * General -> Boot Sequence -> Boot List Option -> Legacy 
  * During the installation be sure to look out for the option to **Install Ubuntu alongside Windows Boot Manager**

## [The Problem](https://davidvielmetter.com/tricks/installing-ubuntu-dual-boot-on-a-dell-precision-which-already-runs-windows-10/)

After shrinking the existing Windows partition within Windows 10 using Disk Manager and creating 256GB of usable space for the new OS, the Ubuntu 18.04 installer cannot find any local hard drives to install the OS.

This is because Dell configures all Windows pre-loaded workstations with *Intel Rapid Storage (RST)* Technology activated. This means that the system UEFI BIOS settings for SATA operation are set to Intel RST RAID as opposed to the more universally recognized Advance Host Controller Interface (AHCI). The Ubuntu installer does not recognize the existing hard drive or partition structure with RST RAID enabled unless additional drivers are provided.

# Issue cased by Etcher
Usually, **Etcher** split the USB disk into 3 partitions. In this URL contains ways to repaire the disk. https://github.com/balena-io/etcher/blob/master/docs/USER-DOCUMENTATION.md#recovering-broken-drives

## Windonws
In Windows, we'll use **diskpart**, a command line utility tool that comes pre-installed in all modern Windows versions.

* Open cmd.exe from either the list of all installed applications, or from the "Run..." dialog usually accessible by pressing Ctrl+X.
* Type **diskpart.exe** and press "Enter". You'll be asked to provide administrator permissions, and a new prompt window will appear. The following commands should be run in the new window.

* Run **list disk** to list the available drives. Take note of the number id that identifies the drive you want to clean.

* Run **select disk N**, where N corresponds to the id from the previous step.

* Run **clean**. This command will completely clean your drive by erasing any existent filesystem.

