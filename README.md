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

