# Windows basic optimization guide in english:

## Some settings may be missing or named differently.

#### 0. Install all available updates:

Go to **Windows Updates** and install all available updates and then reboot. After that pause it for 5 weeks.

#### 1. Disable automatic driver updates:

- WIN+R → **regedit** → **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows** → Create a section named **WindowsUpdate** → And in it create a Dword32 parameter named **ExcludeWUDriversInQualityUpdate** with the value **1**.
- Then go to **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\DriverSearching** find **SearchOrderConfig** and set the value to **0**.

#### 2. Installing Drivers:

1.  Install the latest drivers for chipset, lan, wifi & bluetooth, sound, GPU (below are instructions for installing a clean driver, you can just install the driver without these instructions).. You can get them from the motherboard website.

##### 2.1. Installing driver for the GPU:

- First uninstall the default driver for the GPU via [DDU](https://www.guru3d.com/download/display-driver-uninstaller-download/), after which the PC will restart. Delete only if you've done step #2.
- Install the driver on the GPU. I suggest installing a clean driver image via [Nvcleanstall (for NVidia)](https://www.techpowerup.com/download/techpowerup-nvcleanstall/) or [Radeon Software Slimmer (for AMD)](https://github.com/GSDragoon/RadeonSoftwareSlimmer/releases).

<details>
<summary>Instruction for Nvcleanstall</summary>
<br>

1. Download the latest GeForce Game Ready Driver for your GPU.
2. Run Nvcleanstall.
3. Click on the Use driver files on disk section and specify the path to the driver.
4. For a clean driver, uncheck all the checkboxes and go to the 5th point.
   :warning: If you need GeForce Experience, HDMI sound and/or USB-C port from the video card:

- For sound over HDMI, check the HD Audio via HDMI checkbox.
- For GeForce Experience, check GeForce Experience, NV Container, Telemetry, NV Backend, NodeJS.
- For USB-C, check the USB-C driver checkbox.
- :warning:If you have a laptop, check Optimus and USB-C!

5. Click _Next_ and in the **Tweaks** tab select **Disable Installer Telemetry, Disable MPO, Perform a clean installation**.
6. Next click **Show Expert Tweaks**, select **Disable Driver Telemetry, Disable Nvidia HD Audio device sleep timer, Disable HDCP**,

- _Enable Message Signaled Interrupts_:
  - Interrupt Policy: **Default**
  - Interrupt Priority: **High**
- _Rebuild digital signature_:
  - **Use method compatible with EasyAntiCheat**
  - **Auto accept driver unsigned warning**

7. Click **Next** and then **Install**, install the driver from the window that appears.
8. **Setup Nvidia panel**, photo with settings is in [repository](https://github.com/HackMeGG/windows11-setup/tree/main/nvidia-panel).
9. Disable power saving: Download [nvidiaProfileInspector](https://github.com/Orbmu2k/nvidiaProfileInspector/releases) → find **Cuda Force P2 State** → **Off** → **Apply Changes**.
10. Lock the video card frequency: Download [MSI Afterburner](https://www.msi.com/Landing/afterburner/graphics-cards) → put "Temp Limit" to the maximum value → application settings → put 3 checkboxes "Unlock/Release/Force..." and apply → press Control + F combination → find the number and click on the point with your frequency → press Control + L combination → close the graph and press apply and the button with "Windows" logo.

You can find the frequency of your GPU at [techpowerup](https://www.techpowerup.com/). Search for your model and go to the page, at the very bottom find your graphics card model, you need the value "**Boost Clock**".

11. Disable MPO: download and run the file [disable_mpo from Nvidia website](https://nvidia.custhelp.com/app/answers/detail/a_id/5157).
12. Switching video card in MSI mode: Download [MSI utility v3](https://www.mediafire.com/file/ewpy1p0rr132thk/MSI_util_v3.zip/file) and run the application as administrator → find your video card and check the "**msi**" box, then click "**Apply**".
</details>

<details>
<summary>Radeon Software Slimmer Instruction</summary>
<br>

1. Download the latest Recommended driver from AMD website.
2. Launch Radeon Software Slimmer.
3. Click on the **Pre Install** section and specify the path to the driver.
4. Specify the path for unpacking (create a new folder and specify it, the folder should be empty).
5. Disable all items in **Scheduled Tasks**.
6. In Packages leave only "**AMD Display Driver; AMD Settings; AMD WVR64; Branding64**" and turn off the rest.
   :warning:If you need HDMI audio, leave: **"HDMI Audio Driver"; "High Definition Audio Controller "**.
   :warning:If you need ReLive recording, leave: **"DVR64"**.
7. Click **Modify Installer** and then **Run Installer**, install the driver from the window that appears.
8. Customize the panel.
</details>

#### 3. Install the required software:

- Install the [Visual C++ AIO package](https://www.techpowerup.com/download/visual-c-redistributable-runtime-package-all-in-one/)
- Install [DirectX](https://www.microsoft.com/en-us/Download/confirmation.aspx?id=35)
- Install [.Net Framework 4.8.1](https://dotnet.microsoft.com/en-us/download/dotnet-framework)
- Install [7zip](https://www.7-zip.org/)
- Optionally install [Java JDK](https://www.oracle.com/cis/java/technologies/downloads/#jdk21-windows)

---

#### 4. Checking system files integrity:

Paste the command into _cmd_ as Administrator:

- **sfc /scannow**
- **DISM /Online /Cleanup-Image /RestoreHealth**

#### 5. Settings:

- Uninstall applications you do not use: Settings → Apps → Installed Apps.
- Windows Search Settings → Find My Files → Classic.
- Settings → Games → Captures → disable all.
- Settings → Games → Enable Game Mode.
- Settings → Privacy → everything off (except microphone and camera if you need them).
- Settings → System → Notifications (uncheck all boxes) → Advanced settings → uncheck all boxes.
- Settings → System → Memory → Memory Control → Disable.
- Settings → System → Sharing → Off.
- Settings → Display → Scale → 100 (recommended).
- Settings → Network and Internet → Ethernet → Metered connection → Disable.
- Settings → Applications → Device Sharing and Application Archive (Off).
- Settings → Applications → Standalone Maps → Disable **Metered connection** and uncheck **Update automatically when connected to network and Wi-Fi**.
- Settings → Special Features → Disable **Visual Effects** and **Transparency Effects**.
- Settings → System → Display → Graphics → Change default graphics settings → Enable HAGS and optimization for windows games.
- Settings → System → Display → Set the maximum refresh rate of your monitor.
- Settings → Update Center → Advanced Options → Delivery Optimization → Disable.
- Settings → Windows Security Center → Reputation-based Protection → All Off.
- Settings → Windows Security Center → **Application and Browser Management** → **Reputation-based Protection** → **Reputation-based Protection Settings** → Disable all items.
- Settings → Windows Security Center → Settings → Notifications → Off.

#### 6. Control Panel:

- Control Panel → Mouse → Uncheck **Enhance pointer accuracy**.
- Control Panel → System and Security → Change UAC settings → Never Notify.
- Control Panel → Network Control Center → Change Adapter Settings → PCM on your LAN/WIFI adapter → Properties → disable everything except QoS and IPv4.
- Control Panel → Disable Firewall.
- Control Panel → "View" on the top right is set to "Icons" → Special Features Center → Keyboard Ease → Uncheck "Enable key sticking" under "Make typing easier" → Apply.
- Control Panel → Power Plan → Maximum Performance → Power Button Actions → Quick Start and Hibernation (OFF).
- Control Panel → Network and Internet → Browser Properties → **Security tab** → **Other button** → **Other** → item **Run programs and unsafe files** → **Enable (unsafe)**

:warning:If there is no "Maximum Performance" mode, then write in cmd (as admin): **powercfg -duplicatescheme e9a42b02-d5df-448d-aa00-03f14749eb61**

- Disabling hibernation in cmd (as admin): **powercfg /h off**

◻️ Tip: Sleep and Hibernation do not reboot the system and do not clear data in memory, so you should disable them.\_

#### 7. Disabling Indexing:

Explorer → Local Disk C → PCM → Properties →

- Uncheck "Allow indexing" and Accept.

#### 8. Performance (Disable animation if you wish):

- Win+R → **sysdm.cpl** → tab **Advanced** → section **Speed** button **Settings** → **Provide best performance** → **Apply**.

#### 9. Services that can be disabled:

SysMain → Displayed name: SysMain \
WSearch → Displayed name: Windows Search \.
DiagTrack → Display name: Connected user experiences and telementry \
TrkWks → Displayed name: Distributed Link Tracking Client \
WerSvc → Displayed name: Windows Error Logging Service\
lfsvc → Displayed name: Geolocation service\
Spooler → Displayed name: Print Manager. Disable if you do not have a printer (including network printers)

#### 10. Disable results from the internet in search:

WIN+R → regedit → **HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Windows\Explorer** → Create a DWORD32bit parameter named **DisableSearchBoxSuggestions** and with a value of **1**.

#### 11. Disable background applications:

Windows 10:
Settings → privacy → background applications → uncheck the box.
Windows 11:
WIN+R → gpedit.msc → Computer Configuration > Administrative Templates > Windows Components > Application Privacy → Allow Windows applications to run in the background → "Enabled" and below set "Force Deny".

#### 12. Disabling Windows Copilot Windows 11:

WIN+R → gpedit.msc → User Configuration > Administrative Templates > Windows Components > Windows Copilot → Disable Windows Copilot select "Enabled".

#### 13. Disabling "VBS (Kernel Isolation, Memory Integrity)":

First check if you have virtualization enabled, because if you do, you will have to disable kernel isolation from **Windows Security**. If you are not using virtualization, you can easily disable it in BIOS. or disable Kernel Isolation in Windows.

**Windows Security → Device Security → Kernel Isolation → Kernel Isolation Information → Memory Integrity → Off**.

#### 14. Configure the network adapter:

- Device Manager → Your network adapter →.
  - Power Management → Uncheck all checkboxes.
  - Disable in the _Advanced_ tab → **Energy Efficient Ethernet; Gigabit Lite; Green Ethernet; Power Saving Mode; Anything with Wake on..."; Anything with Offload ...**.

#### 15. Disabling PowerThrottling:

:warning:Use for desktop PCs only!

> WIN+R → regedit → **Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power\PowerThrottling** → **PowerThrottlingOff** → **1** .

#### 16. Disable automatic restarting of applications at system startup:

Settings → Accounts → Logon Options → Disable the "Automatically save my restarted applications and restart them when I log on again" switch.

:white_medium_square: Tip: Windows 11 can save and restart certain applications when you restart your computer and log on. However, if you want to improve the speed of your computer, it is better to disable this feature.

#### 17. Disabling Wi-Fi Sense:

:triangular*flag_on_post: \_Wi-Fi Sense* was a Windows tool designed to collect data about public Wi-Fi hotspots, such as in coffee shops or public buildings. It collected useful data about the access point, such as speed and signal strength, and loaded it into a database

- WIN+R → **regedit** → **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WcmSvc\wifinetworkmanager\config** → **AutoConnectAllowedOEM** → **0**.

#### 18. Disable Microsoft Store apps auto-update:

**Microsoft Store** → click the profile icon → **Application Settings** → **Application Update** → switch to "**Off**".

#### 19. Disabling Hyper-V:

Hyper-V is a virtualization tool embedded in Windows. Unfortunately, Hyper-V can conflict with third-party apps on your PC, including other virtualization tools such as VMWare Workstation, VirtualBox, and emulators. As a result, you may encounter the Hyper-V error when trying to launch an app, games, or hardware tuning utilities. So, if you need to use third-party virtualization software, including VMware WorkStation and Virtual Box, you must disable the Hyper-V Hypervisor.

- To disable:
  - WIN+R → cmd → **bcdedit /set hypervisorlaunchtype off**
- To enable:
  - WIN+R → cmd → **bcdedit /set hypervisorlaunchtype auto**

#### 20. Windows 11 classic right-click context menu & disable menu show delay:

- WIN+R → **regedit** → **HKEY_CURRENT_USER\SOFTWARE\CLASSES\CLSID** → New _Key_ **{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}** → Right-click the newly created key and create one more key named **InprocServer32**, and value of string **(Default)** must be blank.
- WIN+R → HKEY_CURRENT_USER\Control Panel\Desktop → **MenuShowDelay** → **0**.

#### 21. Stop Windows Spying:

:warning: It will broke Windows Defender Smart App Control! If you use Defender skip this step.

- WIN+R → gpedit.msc → Computer Configuration → Administrative Templates → Windows Components → Data Collection and Preview Builds → Allow Diagnostic Data → **Enabled** → **Diagnostic Data off**.
- WIN+R → gpedit.msc → Computer Configuration → Administrative Templates → Windows Components → Data Collection and Preview Builds → Limit optional diagnostic data for Desktop Analytics → **Enabled** → **Disable Desktop Analytics collection**.

#### 22. Clean the system:

- WIN+R → **%temp%** → Delete everything.
- WIN+R → **temp** → Delete everything.
- WIN+R → **prefetch** → Delete everything.
- This PC → Disk C → Windows → SoftwareDistribution → Download → Delete everything.
- Search for **Disk Cleanup** → Disk C → Pin them all → OK.
- WIN+R → **cmd** → ipconfig /flushdns

#### 23. Disable unnecessary applications startup.

#### Additional software:

- Activating Windows forever (Powershell command): **irm https://massgrave.dev/get | iex**
- Defender Remover: https://github.com/ionuttbara/windows-defender-remover/releases
- DISM++: https://www.majorgeeks.com/files/details/dism.html
- Autoruns: https://learn.microsoft.com/en-us/sysinternals/downloads/autoruns
- DeviceCleanup: https://www.majorgeeks.com/files/details/device_cleanup_tool.html
- A good free antivirus: https://download.geo.drweb.com/pub/drweb/cureit/cureit.exe
- explorerpatcher for Windows 11 customization/customization :warning:Warning, problems may occur (crash, blue screen) https://github.com/valinet/ExplorerPatcher
