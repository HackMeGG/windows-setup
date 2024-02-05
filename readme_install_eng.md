# Create a boot drive for Windows 10/11 installation
## I’ll tell you three ways.
### We will need a working PC and a flash drive with a capacity of at least 8GB.

ISO image of the system can be taken from the first way or from other sites of type https://bobpony.com/downloads/ .


#### :small_blue_diamond:First Way - Media Creation Tool
:heavy_check_mark:Media Creation Tool is an official installer, easy to use, always downloads the latest version of Windows. I recommend using this method.

Download the Media Creation Tool:
- For [**Windows 10**](https://www.microsoft.com/en-us/software-download/windows10)
- For [**Windows 11**](https://www.microsoft.com/software-download/windows11)

After running Microsoft, accept the license terms, select **«Create Installation Media»**, then specify the language and version of Windows you want to install.
In the next window there are two choices:
- ISO-file -> is downloaded ISO file where you can install the second or third way.
- USB flash drive -> create a ready flash drive from Windows. **In this case we will choose this item**.

Specify the attached flash drive and wait for the recording to be completed.

#### :small_blue_diamond:The second way - Rufus
Download the **Rufus** and ISO image of the system you need.
Run **Rufus**.
Under Device, select your USB drive.
Under Download method, click "SELECT".
Go to the folder and select the Windows ISO image.
Click the "Open" button.
Under Partition schema, select the option **GPT**.
Under Target System, select **UEFI (non CSM)**.
Under Filesystem, specify **FAT32**.
Click Show Advanced Formatting Options, and ensure that the "Fast Formatting" and "Create Extended Label and Device Icon" labels are marked.
Press the "START" button.
Click "OK" to confirm that the USB flash drive will be cleaned.
After performing these steps, the Rufus tool will create UEFI-enabled Windows boot media.

#### :small_blue_diamond:Third way - Ventoy
Download [Ventoy](https://github.com/ventoy/Ventoy/releases) and ISO image.\
:white_check_mark:With *Ventoy* you can download multiple images, let’s say Windows 10 and 11. The main thing would be enough space on the external drive.\
Start Ventoy2Disk. You can select a language from the menu at the top of the program.\
In the "Device" tab, select your external drive.\
To install *Windows 11* make sure that the "Options" tab has a checkmark for *"Secure Boot" support*.\
Click Install.\
The drive will split into two sections. One will have Ventoy files and the other will be empty.\
Copy the ISO boot files to an empty partition.\
:warning: If, when booting from a flash drive, when selecting an ISO image, an error **"Verification Failed: (15) Access Denied"**: Press "OK" -> Press any key -> "Enroll key from disk" -> "VTOYEFI" -> ""ENROLL_THIS_KEY_IN_MOKMANAGER.cer" -> Continue -> Yes -> Reboot. The PC will reboot, re-select this ISO image and now it will boot normally. 

#### :heavy_exclamation_mark:Once Windows is installed, there are no other partitions:
Right click on «Start» and select «Disk Management».\
All disks and partitions will appear.
- Note whether there is *section* without letter. If you have found the desired partition then click on it with the right mouse button and select "Change drive letter or path to disk", after click «Add». Select a letter and press "OK".
- If the partition is "Not Distributed", right-click the unallocated area and select "Create Simple Volume".
