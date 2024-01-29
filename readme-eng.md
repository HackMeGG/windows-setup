## Windows Customization Guide in Russian:
## This guide is based on Windows 11 settings, so some settings may not be available or may be called differently in Windows 10.
#### 0. Install all available updates
Go to **Windows Update** and install all available updates.
#### 1. Disable automatic driver updates:
- WIN+R -> **regedit** -> **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows** -> Create a section (*folder*) **WindowsUpdate** -> And in it create a Dword32 parameter named **ExcludeWUDriversInQualityUpdate** with the value **1**.
- Then go to **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\DriverSearching** find **SearchOrderConfig** and set the value to **0**. 
#### 2. Installing Drivers
 1) Install the latest drivers for chipset, lan, wifi & bluetooth, sound, you can get them from the motherboard website.
#### 3. Installing the driver for the GPU
   - First uninstall the default driver for the GPU via DDU, after which the PC will restart itself.
   - Install the GPU drivers using Nvcleanstall (for nvidia) or Radeon Software Slimmer (for AMD).
___
> Nvcleaninstall instructions:
1) Download the latest GeForce Game Ready Driver for your GPU.
2) Run Nvcleaninstall.
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
10) Customize the panel (photo with settings in the repository)
___

>Tutorial for Radeon Software Slimmer:
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
#### 4. Install the required software:
* Install the [Visual C++ AIO] package(https://www.techpowerup.com/download/visual-c-redistributable-runtime-package-all-in-one/)
* Install [DirectX](https://www.microsoft.com/en-us/Download/confirmation.aspx?id=35)
* Install [.Net Framework 4.8.1](https://dotnet.microsoft.com/en-us/download/dotnet-framework)
* Install [7zip](https://www.7-zip.org/)
* Optionally install [Java JDK](https://www.oracle.com/cis/java/technologies/downloads/#jdk21-windows)
___
#### 5. Check system files
- Paste the command into CMD as Administrator: **DISM/Online/Cleanup-Image/ScanHealth**
#### 6. Settings: 
- Uninstall UWP apps you don't use: Settings -> Apps -> Installed Apps.
- Windows Search Settings -> Find My Files -> Classic.
- Settings -> Games -> Captures -> disable all.
- Settings -> Games -> Enable game mode.
- Settings -> Privacy -> everything off (except microphone and camera if you need them).
- Settings -> System -> Notifications (uncheck all checkboxes) -> Advanced settings -> uncheck all checkboxes.
- Settings -> System -> Memory -> Memory Control -> Disable.
- Settings -> System -> Sharing -> OFF.
- Settings -> Applications -> Device Sharing and Application Archive (Off).
- Settings -> Windows Security Center -> Settings -> Notifications -> Off.
- Settings -> Special Features -> Disable **Visual Effects** and **Transparency Effects**.
- Settings -> System -> Display -> Graphics -> Change default graphics settings -> Enable HAGS and optimization for windows games.
- Settings -> System -> Display -> Set the maximum refresh rate of your monitor.
- Settings -> Windows Security Center -> Reputation-based protection -> All off.
- Settings -> Windows Security Center -> **Application and Browser Management** -> **Reputation-based Protection** -> **Reputation-based Protection Settings** -> Disable all items.
- Settings -> Update Center -> Advanced Options -> Delivery Optimization -> Disable.
#### 7. Control Panel:
- Control Panel -> Mouse -> uncheck **Enhance pointer accuracy**.
- Control Panel -> System and Security -> Change UAC settings -> Never Notify.
- Control Panel -> Network Control Center -> Change Adapter Settings -> PCM on your LAN/WIFI adapter -> Properties -> disable everything except QoS and IPv4.
- Control Panel -> Disable Firewall.
- Control Panel -> Power Plan -> Maximum Performance -> Power Button Actions -> fast startup and hibernation (OFF).
 
>:warning:If there is no "Maximum Performance" mode then write in cmd (as admin): **powercfg -duplicatescheme e9a42b02-d5df-448d-aa00-03f14749eb61**

- Disabling hibernation in cmd (as admin): **powercfg /h off**

:white_medium_square:*Tip: Sleep or Hibernation mode does not reboot the system and does not clear data in memory, so it is worth disabling them.*
#### 8. Disabling Indexing
   Explorer -> Local Disk C -> PCM -> Properties -> 
  - Uncheck "Allow indexing" and Accept.
  
  After disabling it we go back
  - Tools tab -> Disk Optimization and Defragmentation -> disabled *(do it manually preferably once a week)*.

#### 9. Performance (Disable animation)
- Win+R -> **sysdm.cpl** -> tab **Advanced** -> section **Speed** button **Settings* -> **Provide best performance** -> **Apply**

#### 10.   Services that can be disabled:
**DiagTrack; TrkWks; WalletService; wisvc; WpcMonSvc; SysMain; VSS; WerSvc; WSearch, lfsvc, Spooler** (Spooler -> if no printer).
#### 11.  Disable results from the internet in search:
WIN+R -> regedit -> **HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Windows\Explorer** -> Create a DWORD32bit parameter named **DisableSearchBoxSuggestions** and with a value of **1**.
#### 12.  Disable background applications: 
WIN+R -> gpedit.msc -> Computer Configuration > Administrative Templates > Windows Components > Application Privacy -> Allow Windows applications to run in the background -> "Enabled" and set "Force Deny" below.
#### 13.  Disabling Windows Copilot:
WIN+R -> gpedit.msc -> User Configuration > Administrative Templates > Windows Components > Windows Copilot -> Disable Windows Copilot select "Enabled".
#### 14. Disable Windows Defender (use all three items):
1) WIN+R -> regedit -> **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender** -> create a Dword32bit named **DisableAntiSpyware** -> value **1**
3) WIN+R -> gpedit.msc -> Computer Configuration > Administrative Templates > Windows Components > Microsoft Defender Antivirus Program -> Disable Microsoft Defender Antivirus Program -> **On**.
4) WIN+R -> gpedit.msc -> Computer Configuration > Administrative Templates > Windows Components > Microsoft Defender Antivirus Program > Persistent Protection -> Disable Persistent Protection -> **Enabled**.
#### 15.  Disabling MPO:
1) Quick way: download and run the [disable_mpo file from Nvidia website](https://nvidia.custhelp.com/app/answers/detail/a_id/5157)
   
:white_check_mark:I recommend the second method, manually.

2) Manually: WIN+R -> regedit -> **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Dwm** -> Create a DWORD32bit parameter with the name **OverlayTestMode** and the value **5**.
#### 16.  Disable Windows GameBar (WIN+G will work), use both steps:
   **Первый шаг**:
   >Проводник -> Диск С -> Windows -> System32 -> GameBarPresenceWriter.exe -> ПКМ -> Вкладка Безопасность -> Дополнительно -> Второй пункт, где Владелец нажмите Изменить -> здесь, где пустое место надо написать имя вашего аккаунта (его можно узнать в Параметры -> Аккаунты -> сверху будет написано имя вашего локального аккаунта или почта если вы ранее вошли в аккаунт) -> После чего написали имя нажмите на Проверить Имена -> Нажмите Применить потом Готово -> нажмите Добавить -> Выберите субъект -> Опять вводите имя пользователя -> Готово -> Во вкладке Общие Разрешения поставьте галочку напротив Полный Доступ -> Применяем и выходим -> Опять заходим -> ПКМ -> Вкладка Безопасность -> Дополнительно -> Второй пункт, где Владелец нажмите Изменить -> вместо нашего имени вводим NT Service\TrustedInstaller -> нажмите на Проверить Имена -> ОК -> Применить -> ОК -> ОК -> Теперь переименуйте файл (просто добавьте в конце несколько цифр).

**Второй шаг**:
>WIN+R -> regedit -> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WindowsRuntime\ActivatableClassId\Windows.Gaming.GameBar.PresenceServer.Internal.PresenceWriter ->ПКМ по папке -> Разрешения -> Добавить -> пишем имя аккаунта -> нажмите на Проверить Имена -> Дополнительно -> где Владелец нажмите Изменить -> пишем имя аккаунта -> нажмите на Проверить Имена -> Применить потом Готово -> Поставьте галочку где Полный Контроль -> Закройте -> измените ActivationType -> значение 0.
#### 17.  Uninstalling Windows 11 widgets 
Powershell command: **winget uninstall "windows web experience pack "** 
#### 18.  Disabling "Kernel Isolation"
First check if you have virtualization enabled, because if you do, you will have to disable kernel isolation from **Windows Security**. If you don't use virtualization, you can disable it in BIOS or disable Kernel Isolation in Windows.
>**Windows Security -> Device Security -> Kernel Isolation -> Kernel Isolation Information -> Memory Integrity -> Off**.
#### 19. Configuring the network adapter
  - Device Manager -> Your network adapter -> 
    - Power Management -> Uncheck all checkboxes. 
    - Disable Advanced tab -> **Energy-Efficient Ethernet; Gigabit Lite; Green Ethernet; Power Saving Mode; Anything with Wake on magic; Shutdown Wake-On-Lan**.

#### 20.  Switching the video card in MSI mode
Download [MSI utility v3](https://www.mediafire.com/file/ewpy1p0rr132thk/MSI_util_v3.zip/file) and run the application as administrator -> find your video card and check the "**msi**" box, then click "**Apply**".
#### 21. Disabling PowerThrottling 
:warning:Use for desktop PCs only!

>WIN+R -> regedit -> **Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power\PowerThrottling** -> **PowerThrottlingOff** -> **1** .
#### 22. Disable unnecessary devices in Device Manager.
Device Manager -> Disable: **Microsoft GS Wavetable Synth; Composite Bus Enumerator; Microsoft Hyper-V Virtualization; Microsoft Virtual Drive Enumerator; NDIS Virtual Network; Remote Desktop Device; UMBus Root Bus Enumerator**.
#### 23. Automatic restart of applications at system startup
Settings -> Accounts -> Login Options -> Disable the switch "Automatically save my restarted applications and restart them when I log in again."

:white_medium_square:Tip: Windows 11 can save and restart certain applications when you restart your computer and log in. However, if you want to improve the speed of your computer, it is better to disable this feature.
#### 24.  Disable Teredo (ipv6 feature causing latency):
- WIN+R -> CMD -> netsh interface teredo set state disabled
(CMD to enable: netsh interface teredo set state default )
#### 25.  How to disable the notification icon in the system tray:
- WIN+R -> gpedit.msc -> User Configuration > Administrative Templates > Start Menu and Taskbar -> Remove Notifications and Action Center -> Enabled -> Apply/OK
#### 26. Disabling Wi-Fi Sense
:triangular_flag_on_post: *Wi-Fi Sense* was a Windows tool designed to collect data about public Wi-Fi hotspots, such as in coffee shops or public buildings. It collected useful data about the access point, such as speed and signal strength, and loaded it into a database
- WIN+R -> **regedit** -> **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WcmSvc\wifinetworkmanager\config** -> **AutoConnectAllowedOEM** -> **0**.
#### 27. Install the programs you need.
#### 28. Disable unnecessary applications from autorun.
#### 29. Clean the system:
- WIN+R -> **%temp%** -> Delete everything.
- WIN+R -> **temp** -> Delete everything.
- WIN+R -> **prefetch** -> Delete everything.
- WIN+R -> **cmd** -> ipconfig /flushdns
#### 30.  Disable FSO:
**Fullscreen Exclusive (FSE)** mode gives your game complete ownership of the display and allocation of resources of your graphics card.

**Fullscreen Optimizations (FSO)** which takes full screen exclusive games and runs them instead in a highly optimized borderless windowed format that takes up the entire screen. 

With FSO you get the visual experience and performance of running your game in FSE, but with the benefits of running in a windowed mode. These benefits include faster PC commands such as alt-tab, multiple monitor set ups and overlays. So if you don't need overlays I reccomend you to disable FSO for your games.
>To disable **FSO**:\
Find the game **.exe** you are trying to play\
Right click on the game and select "**Properties**"  
Click "**Compatibility**" tab\
CHECK the "**Disable fullscreen optimizations**" \
hit **APPLY** and **OK** button.

#### 31.  Enabling ReBar:
ReBar (resizable BAR) enables more efficient communication between the CPU and the graphics card. Enabling this functionality can result in a performance improvement. For AMD ReBar is named SAM, it's the same thing as ReBar.

:warning: To use ReBar, you need a **NVIDIA GeForce RTX 30-series** or **AMD RX 6000 series**, a compatible **CPU**, compatible **motherboard**.

- To enable Resizable BAR:
  - Enter the system’s BIOS configuration
  - Disable **Compatibility Support Module (CSM) / Legacy Mode** and enable **UEFI** boot mode.
  - Enable (or check Auto if the Enabled option is not present):\
      *They are often found in the PCIe Subsystem settings*
    - Above 4G Decoding
    - Re-Size BAR Support
- To check if it's working check in NVIDIA Control Panle or in AMD Control Panel. 


#### 32.  Additional software:
- Activating Windows Forever (Powershell command): irm https://massgrave.dev/get | iex
- Windows Defender Removal: https://github.com/ionuttbara/windows-defender-remover
- Remove Edge: https://github.com/ShadowWhisperer/Remove-MS-Edge
- AllInOne ToolBox: https://github.com/ChrisTitusTech/winutil
- O&O ShutUp10++: https://www.oo-software.com/en/shutup10
- DISM++: https://github.com/Chuyu-Team/Dism-Multi-language/releases
- Autoruns: https://learn.microsoft.com/en-us/sysinternals/downloads/autoruns
- DeviceCleanup: https://www.majorgeeks.com/files/details/device_cleanup_tool.html
- explorerpatcher for Windows 11 customization/customization :warning:Warning, problems may occur (crash, blue screen) https://github.com/valinet/ExplorerPatcher
