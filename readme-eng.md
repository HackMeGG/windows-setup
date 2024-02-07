# Windows Basic Optimization Guide in English:
## This guide is based on Windows 11 settings, so some settings may not be available or may be named differently in Windows 10.
#### 0. Install all available updates:
Go to **Windows Update** and install all available updates.
#### 1. Activate Windows permanently 
Copy the command into *Powershell* (as administrator) without brackets: "**irm https://massgrave.dev/get | iex**".
#### 2. Disable automatic driver updates:
- WIN+R → **regedit** → **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows** → Create a section named **WindowsUpdate** → And in it create a Dword32 parameter named **ExcludeWUDriversInQualityUpdate** with the value **1**.
- Then go to **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\DriverSearching** find **SearchOrderConfig** and set the value to **0**. 
#### 3. Installing Drivers:
 1) Install the latest drivers for chipset, lan, wifi & bluetooth, sound. You can get them from the motherboard website.
#### 4. Installing the driver for the GPU:
   - First uninstall the default driver for the GPU via DDU, after which the PC will restart.
   - Install the GPU drivers using Nvcleanstall (for nvidia) or Radeon Software Slimmer (for AMD).
  >:arrow_right:Nvcleanstall instruction:
1) Download the latest GeForce Game Ready Driver for your GPU.
2) Run Nvcleanstall.
3) Click on the Use driver files on disk section and specify the path to the driver.
4) Uncheck all the checkboxes and go to the 8th item.
   
   :warning: If you need GeForce Experience, audio via HDMI and/or USB-C port from your video card, please read step 5-7.
5) For HDMI audio, check the HD Audio via HDMI checkbox.
6) For GeForce Experience, check GeForce Experience, NV Container, Telemetry, NV Backend, NodeJS.
7) For USB-C, check the USB-C driver checkbox.
   
    :warning:If you have a laptop, check Optimus and USB-C!

8) Click *Next* and in the **Tweaks** tab select **Disable Installer Telemetry, Disable MPO**. 
   
   :triangular_flag_on_post:If you haven't uninstalled the old driver via DDU before, check **Perform a clean installation**. 
   
   Next, click **Show Expert Tweaks**, select Disable Driver Telemetry, Disable Nvidia HD Audio device sleep timer, Disable HDCP,  
    >Enable Message Signaled Interrupts 
    >>* Interrupt Policy: **Default** 
    >>* Interrupt Priority: **High**

    >Rebuild digital signature 
    >>* **Use method compatible with EasyAntiCheat**. 
    >>* **Auto accept driver unsigned warning**.

9)  Click **Next** and then **Install**, install the driver from the window that appears.
10) Customize the panel, photo with settings in the [repository](https://github.com/HackMeGG/windows11-setup/tree/main/nvidia-panel)
___

>Radeon Software Slimmer instruction:
1) Download the latest Recommended driver from the AMD website.
2) Launch Radeon Software Slimmer.
3) Click on the **Pre Install** section and specify the path to the driver.
4) Specify the path to unpack the driver (create a new folder and specify it, the folder must be empty).
5) Disable all items in Scheduled Tasks.
6) In Packages leave only "**AMD Display Driver; AMD Settings; AMD WVR64; Branding64**", and turn off the rest.
 
:warning:If you need HDMI audio, leave: **"HDMI Audio Driver"; "High Definition Audio Controller "**.

:warning:If you need ReLive recording, leave: **"DVR64"**.

7) Click **Modify Installer** and then **Run Installer**, install the driver from the window that appears.
8) Customize the panel (photo with settings in the repository)
___
#### 5. Install the required software:
* Install the [Visual C++ AIO package](https://www.techpowerup.com/download/visual-c-redistributable-runtime-package-all-in-one/)
* Install [DirectX](https://www.microsoft.com/en-us/Download/confirmation.aspx?id=35)
* Install [.Net Framework 4.8.1](https://dotnet.microsoft.com/en-us/download/dotnet-framework)
* Install [.Net Framework 8.0.1](https://download.visualstudio.microsoft.com/download/pr/f18288f6-1732-415b-b577-7fb46510479a/a98239f751a7aed31bc4aa12f348a9bf/windowsdesktop-runtime-8.0.1-win-x64.exe)
* Install [7zip](https://www.7-zip.org/)
* Optionally install [Java JDK](https://www.oracle.com/cis/java/technologies/downloads/#jdk21-windows)
___
#### 6. Checking system files integrity:
Paste the commands into CMD as Administrator:
- **sfc /scannow**
- **DISM /Online /Cleanup-Image /RestoreHealth**
#### 7. Settings: 
- Uninstall apps you don't use: Settings → Apps → Installed Apps.
- Windows Search Settings → Find My Files → Classic.
- Settings → Games → Captures → disable all.
- Settings → Games → Enable game mode.
- Settings → Privacy → everything off (except microphone and camera if you need them).
- Settings → System → Notifications (uncheck all checkboxes) → Advanced settings → uncheck all checkboxes.
- Settings → System → Memory → Memory Control → Disable.
- Settings → System → Sharing → OFF.
- Settings → Display → Scale → 100 (recommended).
- Settings → Applications → Device Sharing and Application Archive (Off).
- Settings → Applications → Offline Maps → Disable **Metered Connection** and uncheck **Update automatically when plugged in and on Wi-Fi** 
- Settings → Windows Security Center → Settings → Notifications → Off.
- Settings → Special Features → Disable **Visual Effects** and **Transparency Effects**.
- Settings → System → Display → Graphics → Change default graphics settings → Enable HAGS and optimization for windows games.
- Settings → System → Display → Set the maximum refresh rate of your monitor.
- Settings → Windows Security Center → Reputation-based protection → All off.
- Settings → Network & internet → Ethernet → Metered Conection → Disable.
- Settings → Windows Security Center → **Application and Browser Management** → **Reputation-based Protection** → **Reputation-based Protection Settings** → Disable all items.
- Settings → Update Center → Advanced Options → Delivery Optimization → Disable.
#### 8. Control Panel:
- Control Panel → Mouse → uncheck **Enhance pointer accuracy**.
- Control Panel → System and Security → Change UAC settings → Never Notify.
- Control Panel → Network Control Center → Change Adapter Settings → right-click on your LAN/WIFI adapter → Properties → disable everything except QoS and IPv4.
- Control Panel → Disable Firewall.
- Control Panel → Power Plan → Maximum Performance (for Intel) / Ryzen High performance (for AMD) → Power Button Actions → fast startup and hibernation (OFF).
 
:warning:If there is no **"Maximum Performance"** mode then write in cmd (as admin): **powercfg -duplicatescheme e9a42b02-d5df-448d-aa00-03f14749eb61**
:warning: Power Plan *Maximum Performance* can cause big temperatures on *notebooks*.
:warning: **Ryzen Power Plans** will appear after you install **chipset** driver and selected Ryzen Power Plans.

#### 9. Disabling hibernation 
Enter the command in cmd (as admin): **powercfg /h off**

:white_medium_square:Hibernation is a temporary shutdown mode, it saves battery power when idle and keeps programs open so the user can get back to work with them quickly.

:white_medium_square:Sleep or Hibernation does not reboot the system or clear data in memory, so it is worth disabling it. Hibernation also reserves some space on the disk for the hiberfil.sys file, which will eventually take up space. Disabling hibernation will also disable the quick start option.

:white_medium_square:The main difference between sleep and hibernation is that in sleep mode the computer continues to consume power to maintain data in RAM. And in hibernation, there is virtually no power consumption. A laptop can spend a long time in this state, and the computer can be unplugged at all, and no data will be lost.
#### 10. Disabling Indexing:
   Explorer → Local Disk C → right-click → Properties → Uncheck "Allow indexing" → Accept.

#### 11. Performance (Disable animation):
- Win+R → **sysdm.cpl** → tab **Advanced** → section **Speed** button **Settings** → **Provide best performance** → **Apply**.

#### 12. Services that can be disabled:
- DiagTrack
- TrkWks
- WalletService 
- wisvc
- WpcMonSvc
- TapiSrv
- PhoneSvc
- MapsBroker
- SysMain
- VSS
- WerSvc
- WSearch
- lfsvc
- WbioSrvc (if you dont use unlock with face or fingerprint)
- Spooler (if no printer) 
- All Hyper-V services (if you dont use it)
- Sensor Service; Sensor Data Service; Sensor Monitoring Service (Disable that 3 services only on Desktop PC)

#### 13. Disable results from the internet in search:
WIN+R → regedit → **HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Windows\Explorer** → Create a DWORD32bit parameter named **DisableSearchBoxSuggestions** and with a value of **1**.
#### 14. Disable background applications: 
WIN+R → gpedit.msc → Computer Configuration > Administrative Templates > Windows Components > Application Privacy → Allow Windows applications to run in the background → "Enabled" and set "Force Deny" below.
#### 15. Disabling Windows Copilot:
WIN+R → gpedit.msc → User Configuration > Administrative Templates > Windows Components > Windows Copilot → Disable Windows Copilot select "Enabled".
#### 16. Disable Windows Defender (use all steps):
:warning: Disabling Defender will improve performance but reduce security. If you care about security use Defender or disable it but use another Antivirus.
1) WIN+R → regedit → **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender** → create a Dword32bit named **DisableAntiSpyware** → value **1**
2) WIN+R → gpedit.msc → Computer Configuration > Administrative Templates > Windows Components > Microsoft Defender Antivirus Program → Disable Microsoft Defender Antivirus Program → **On**.
3) WIN+R → gpedit.msc → Computer Configuration > Administrative Templates > Windows Components > Microsoft Defender Antivirus Program > Persistent Protection → Disable Persistent Protection → **Enabled**.
#### 17. Disabling MPO:
1) Quick way: download and run the [disable_mpo file from Nvidia website](https://nvidia.custhelp.com/app/answers/detail/a_id/5157)
   
:white_check_mark:I recommend the second method, manually.

2) Manually: WIN+R → regedit → **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Dwm** → Create a DWORD32bit parameter with the name **OverlayTestMode** and the value **5**.
#### 18.  Disable Windows GameBar (WIN+G will work), use both steps:
**First Step**:
- Rename GameBarPresenceWriter.exe:
   >Explorer → Disk C → Windows → System32 → GameBarPresenceWriter. exe → right-click → Security tab → Advanced → Second item, where Owner click Edit → here, where there is an empty space you should write the name of your account (you can find it in Settings → Accounts → the name of your local account or mail, will be written at the top if you have previously logged into the account) → After you have entered the name, click Check Names → Click Apply then Done → click Add → Select Subject → Enter the user account name again → Done → In the General Permissions tab, check the Full Access checkbox → Apply and exit → Go in again → right-click → Security tab → Advanced → Second item where Owner click Change → instead of our name enter NT Service\TrustedInstaller → click on Check Names → OK → Apply → OK → OK → OK → Now rename the file (just add some numbers at the end).
   
**Second step**:
- HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WindowsRuntime\ActivatableClassId\Windows.Gaming.GameBar.PresenceServer.Internal.PresenceWriter → ActivationType → value 0.
   >WIN+R → regedit → HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WindowsRuntime\ActivatableClassId\Windows.Gaming.GameBar.PresenceServer.Internal. PresenceWriter → right-click on the folder → Permissions → Add → write the account name → click on "Check Names" → Advanced → where "Owner" is click on "Change" → retype the account name → click on "Check Names" → Apply then Done → Check the box where Full Control → Close → change the ActivationType → value 0.

#### 19.  Uninstalling Windows 11 widgets:
Powershell command: **winget uninstall "windows web experience pack"** 
#### 20.  Disabling "VBS (Core Isolation, Memory Integrity)":
First check if you have virtualization enabled, because if you do, you will have to disable Core isolation from **Windows Security**. If you don't use virtualization, you can disable it in BIOS or disable Core Isolation in Windows.
>**Windows Security → Device Security → Core Isolation → Core Isolation Information → Memory Integrity → Off**.
#### 21. Configuring the network adapter:
  - Device Manager → Your network adapter → 
    - Power Management → Uncheck all checkboxes. 
    - Disable Advanced tab → **Energy-Efficient Ethernet; Gigabit Lite; Green Ethernet; Power Saving Mode; Anything with Wake on magic; Shutdown Wake-On-Lan**.

#### 22.  Switching the video card in MSI mode:
Download [MSI utility v3](https://www.mediafire.com/file/ewpy1p0rr132thk/MSI_util_v3.zip/file) and run the application as administrator → find your video card and check the "**msi**" box, then click "**Apply**".
#### 23. Disabling PowerThrottling:
:warning:Use for desktop PCs only! On notebook's can cause big temperatures.

>WIN+R → regedit → **Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power\PowerThrottling** → **PowerThrottlingOff** → **1**
#### 24. Disable unnecessary devices in Device Manager:
Device Manager → Disable:
- Microsoft GS Wavetable Synth
- Composite Bus Enumerator
- Microsoft Hyper-V Virtualization
- Microsoft Virtual Drive Enumerator
- NDIS Virtual Network
- Remote Desktop Device
- UMBus Root Bus Enumerator
#### 25. Automatic restart of applications at system startup:
Settings → Accounts → Login Options → Disable the switch "Automatically save my restarted applications and restart them when I log in again."

:white_medium_square:Tip: Windows 11 can save and restart certain applications when you restart your computer and log in. However, if you want to improve the speed of your computer, it is better to disable this feature.
#### 26. Disable Teredo (ipv6 feature causing latency):
- WIN+R → CMD → netsh interface teredo set state disabled
(CMD to enable: netsh interface teredo set state default )
#### 27. Disabling notification icon in the system tray:
- WIN+R → gpedit.msc → User Configuration > Administrative Templates > Start Menu and Taskbar → Remove Notifications and Action Center → Enabled → Apply/OK
#### 28. Disabling Wi-Fi Sense:
:triangular_flag_on_post: *Wi-Fi Sense* was a Windows tool designed to collect data about public Wi-Fi hotspots, such as in coffee shops or public buildings. It collected useful data about the access point, such as speed and signal strength, and loaded it into a database.
- WIN+R → **regedit** → **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WcmSvc\wifinetworkmanager\config** → **AutoConnectAllowedOEM** → **0**.
#### 29. Install the programs you need.
#### 30. Disable unnecessary applications from autorun.
#### 31. Clean the system:
- WIN+R → **%temp%** → Delete everything.
- WIN+R → **temp** → Delete everything.
- WIN+R → **prefetch** → Delete everything.
- This PC → Disk C → Windows → SoftwareDistribution → Download → Delete everything.
- Search for **Disk Cleanup** → Disk C → Pin them all → OK.
- WIN+R → **cmd** → ipconfig /flushdns
#### 32.  Disable FSO:
**Fullscreen Exclusive (FSE)** mode gives your game complete ownership of the display and allocation of resources of your graphics card.

**Fullscreen Optimizations (FSO)** which takes full screen exclusive games and runs them instead in a highly optimized borderless windowed format that takes up the entire screen. 

With FSO you get the visual experience and performance of running your game in FSE, but with the benefits of running in a windowed mode. These benefits include faster PC commands such as alt-tab, multiple monitor set ups and overlays. So if you don't need overlays I reccomend you to disable FSO for your games.

To disable **FSO**:\
Find the game **.exe** you are trying to play\
Right click on the game and select "**Properties**"  
Click "**Compatibility**" tab\
CHECK the "**Disable fullscreen optimizations**" \
hit **APPLY** and **OK** button.

**Disable FSO globally**:\
You can disable FSO globally so you don't have to disable it for each application:\
>WIN + R → regedit → **HKEY_CURRENT_USER\System\GameConfigStore** → **GameDVR_FSEBehavior** (*Dword32bit*)→ value: **2** (off) / **0** (on).

#### 33. Disable Microsoft Store apps auto-update:
**Microsoft Store** → click the profile icon → **Application Settings** → **Application Update** → switch to "**Off**".

#### 34. Disable sticky keys:
Control Panel → Ease of Access → Ease of Access Center → Make the Keyboard Easier To Use → Under “Make it Easier To Type” → uncheck the “Turn on Sticky Keys” → Apply.

#### 35. Disabling Hyper-V:
Hyper-V is a virtualization tool embedded in Windows. Unfortunately, Hyper-V can conflict with third-party apps on your PC, including other virtualization tools such as VMWare Workstation, VirtualBox, and emulators. As a result, you may encounter the Hyper-V error when trying to launch an app, games, or hardware tuning utilities. So, if you need to use third-party virtualization software, including VMware WorkStation and Virtual Box, you must disable the Hyper-V Hypervisor.
- To disable:
  - WIN+R → cmd → **bcdedit /set hypervisorlaunchtype off**
- To enable:
  - WIN+R → cmd → **bcdedit /set hypervisorlaunchtype auto**

#### 36. Stop Windows Spying №1:
:warning: It will broke Windows Defender Smart App Control! If you use Defender skip this step.
- WIN+R → gpedit.msc → Computer Configuration → Administrative Templates → Windows Components → Data Collection and Preview Builds → Allow Diagnostic Data → **Enabled** → **Diagnostic Data off**.
- WIN+R → gpedit.msc → Computer Configuration → Administrative Templates → Windows Components → Data Collection and Preview Builds → Limit optional diagnostic data for Desktop Analytics → **Enabled** → **Disable Desktop Analytics collection**.
#### 37. Stop Windows Spying №2:
For this we will need the program **[O&O ShutUp10++](https://www.oo-software.com/en/shutup10)**. We will use it to disable some of the Windows 10 and 11 spyware services.
#### 38. Setup Audio:
Settings → System → Sound → More sound settings → keep only your speaker/headset and microphone, rest disable. Set your speaker/headset device to 24bit 96000Hz. In "Communications" tab set "Do nothing". Double-click on your output device (headset/speaker) go to "Advanced" and uncheck "Allow apps to take exclusive control of this device", apply changes.

#### 39. Defrag & Trim:
Leave enable or disable but do it manually once at week, defrag your HDD's and trim your SSD's. 
To open menu with that setting: \
-  This PC → right click on a disk → properties → tools → Optimize and defrag drive.
#### 40. Disabling Windows Diagnostics:
The Diagnostic Service allows you to detect and troubleshoot problems related to Windows. The services are just running all the time and are of no use.
First, you need to disable the services:
- Diagnostic Policy Service (DPS)
- Diagnostic Service Host (WdiServiceHost)
- Diagnostic system node (WdiSystemHost).

Then change the values in the registry:
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\WMI\Autologger\DiagLog → Start → 0.
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\WMI\Autologger\WdiContextLog → Start → 0

:warning:After that, the network utilization indicator in Task Manager will not work.
#### 41. Windows 11 classic right-click context menu & disable menu show delay:
  - WIN+R → **regedit** → **HKEY_CURRENT_USER\SOFTWARE\CLASSES\CLSID** → New *Key* **{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}** → Right-click the newly created key and create one more key named **InprocServer32**, and value of string **(Default)** must be blank.
  - WIN+R → HKEY_CURRENT_USER\Control Panel\Desktop → **MenuShowDelay** → **0**. 

#### 42. Windows 11 wallpaper compression:
By default, Windows will compress images to around 80-85% before you set them as wallpapers. However, this can sometimes result in blurry images. It doesn't affect performance.
- **To disable compression**:
WIN+R → **regedit** → **HKEY_CURRENT_USER\Control Panel\Desktop** → New DWORD(32-bit) **JPEGImportQuality** → Choose **Base** as **Decimal** and click **OK**. After change the **Value** to **100**. Restart PC and re-upload your background.
- **To revert** the changes, change the DWORD **Value** data to **0**.

#### 43. ReBar / SAM:
ReBar (resizable BAR) enables more efficient communication between the CPU and the graphics card. Enabling this functionality can result in a performance improvement. For AMD ReBar is named SAM, it's the same thing as ReBar.

:warning: To use *ReBar*, you will need a **NVIDIA GeForce RTX 30-series** or **Intel Arc**, a compatible **processor** (10th generation Intel processors or newer), and a compatible **motherboard**.
:warning: To use *SAM*, you will need a **AMD RX 6000-series**, a compatible **Ryzen 5000 or 3000-series processor** (except Ryzen 5 3400G and Ryzen 3 3200G), and a **Motherboard with a 500-series chipset**.

- To enable Resizable BAR:
  - Enter the system’s BIOS configuration
  - Disable **Compatibility Support Module (CSM) / Legacy Mode** and enable **UEFI** boot mode.
  - Enable (or check Auto if the Enabled option is not present):\
      *They are often found in the PCIe Subsystem settings*
    - Above 4G Decoding
    - Re-Size BAR Support
- To check if it's working check in NVIDIA Control Panle or in AMD Control Panel. 

#### Additional software:
- Defender Remover: https://github.com/ionuttbara/windows-defender-remover/releases
- DISM++: https://github.com/Chuyu-Team/Dism-Multi-language/releases
- Autoruns: https://learn.microsoft.com/en-us/sysinternals/downloads/autoruns
- DeviceCleanup: https://www.majorgeeks.com/files/details/device_cleanup_tool.html
- A good free antivirus: https://download.geo.drweb.com/pub/drweb/cureit/cureit.exe
- explorerpatcher for Windows 11 customization :warning:Warning, problems may occur: https://github.com/valinet/ExplorerPatcher
