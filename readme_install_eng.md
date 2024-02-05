# Create a boot drive for Windows 10/11 installation
## I’ll tell you three ways.
### We will need a working PC and a flash drive with a capacity of at least 8GB.
___
ISO images of the systems can be taken from the first way or from other sites of type https://bobpony.com/downloads/ .


:heavy_check_mark:Media Creation Tool is the official installer, it is easy to use, always downloads the latest version of Windows. I recommend using this method.

Download Media Creation Tool:
- For [**Windows 10**](https://www.microsoft.com/ru-ru/software-download/windows10)
- For [**Windows 11**](https://www.microsoft.com/ru-ru/software-download/windows11)
1. Run Media Creation Tool
2. Accept the license terms
3. Select **"Create installation media "**.
4. Specify the language and version of Windows you want to install.
5. In the next window there will be two choices:
- ISO file -> an ISO file will be downloaded where you can install using the second or third method.
- USB flash memory device -> create a ready-made flash drive with Windows. **In this case we will choose this option**.

6. Specify the connected flash drive and wait for the writing to the flash drive to complete.
___
#### :small_blue_diamond:Second method - Rufus
1. Download **Rufus** and the ISO image of the system you want.
2. Run **Rufus**.
3. In the Device section, select your USB drive.
4. In the Boot Method section, click the SELECT button.
5. Navigate to the folder and select the ISO image with Windows.
6. Click the "Open" button.
7. Under Partition Layout, select the **GPT** option.
8. Under Target System, select the **UEFI (non CSM)** option.
9. In the File System section, select **FAT32**.
10. Click the Show Advanced Formatting Options button and make sure the "Quick Formatting" and "Create Advanced Device Label and Icon" labels are checked.
11. Click the START button.
12. Click the "OK" button to confirm that the USB flash memory device will be cleared.
13. After following these steps, the Rufus tool will create a UEFI-enabled Windows bootable media.
___
#### :small_blue_diamond:The third method is Ventoy.

:white_check_mark:With *Ventoy* you can download several images, let's say Windows 10 and 11. The main thing is to have enough space on the external drive.

1. Download [Ventoy](https://github.com/ventoy/Ventoy/releases) and ISO image.
2. Run Ventoy2Disk. In the program at the top of the menu you can select the language.
3. In the "Device" tab, select your external drive.
To install *Windows 11*, make sure that *"Support Secure Boot "* is checked in the "Options" tab.
1. Click install.
The drive will split into two partitions. One will have the Ventoy files on it and the other will be empty.
1. Copy the ISO boot files to the empty partition.

:warning: If you get an error **"Verification Failed: (15) Access Denied "** when selecting the ISO image when booting from the flash drive: \
Press "OK" -> Press any key -> "Enroll key from disk" -> "VTOYEFI" -> "ENROLL_THIS_KEY_IN_MOKMANAGER.cer" -> Continue -> Yes -> Reboot. PC will reboot, re-select this ISO image and now it will boot normally. 
___
#### :heavy_exclamation_mark:Once Windows is installed, there are no other partitions:
Right click on «Start» and select «Disk Management».\
All disks and partitions will appear.
- Note whether there is *section* without letter. If you have found the desired partition then click on it with the right mouse button and select "Change drive letter or path to disk", after click «Add». Select a letter and press "OK".
- If the partition is "Not Distributed", right-click the unallocated area and select "Create Simple Volume".

#### Example of UEFI and Legacy BIOS
![Example of UEFI and Legacy BIOS](https://github.com/HackMeGG/windows11-setup/blob/main/bios-legacy-uefi.jpg)
