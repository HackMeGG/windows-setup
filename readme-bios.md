My BIOS settings for MSI Tomagawk Max II:


-Essential settings:
PCI Subsystem Settings

ReSize Bar Support - Enabled
Above 4G memory/crypto C m - Auto Enabled by ReBar
PCI_E1 Gen Switch - Select highest Gen
Chipset Gen Switch - Select highest Gen
PCIe x1 Slot Switch - Select highest Gen

Integrated Peripherals

VGA Card Detection - ignore
Onboard LAN Controller - Enabled
HD Audio Controller - Disabled if using USB audio, otherwise leave Enabled

USB Configuration

XHCI Hand-off - Disabled
Legacy USB Support - Disabled ( Enable again to install Windows and if your mouse/Keyboard doesn't work in the OS )

Super IO Config

Serial Com Port 0 Config - Disabled
Parallel LPT Port Config - Disabled

Power Management Setup

ErP Ready - Disabled
System Power Fault Protection - Disabled

AMD Overclocking →DDR & Infinity Fabric F/T → DDR Frequency and Timings  →  DRAM Controller Config  →  DRAM Power Options

Power Down Enable - Disabled
Gear Down Mode - Disabled ( Set 2T parameter from Auto to T1 if you want to disable the setting, leave it if you cant)

ACPI Settings

CPU Over Temperature Alert - Disabled


Wake Up Event Setup

Wake Up Event By - [Bios]
Resume By RTC Alarm - Disabled
Resume By PCI-E Device - Disabled
Resume By USB Device - Disabled
Resume From S3/S4/S5 B PS/Mouse - Disabled
Resume From S3/S4/S5 B PS/Keyboard - Disabled

Trusted Computing

First Enable Security Device Support- switch amd ftpm switch to amd ftpm disabled then disable Security Device Support


Chassis Intrusion Config
Chassis Intrusion - Disabled


Full Screen Logo Display - Disabled
Bootup NumLock State - Off
Info Block effect - Lock
Post Beep - Disabled


OC Explorer Mode [Expert]

Advanced CPU Config

SVM Mode - Disabled ( Used for Virtual Machine so Enable if you need)
NX Mode - Disabled  ( Could cause a Vanguard error for Valorant. If so, turn the setting to Enabled)
PSS Support - Disabled
AMD Cool and quiet - Disabled
Spread Spectrum - Disabled
Performance Regulator - Disabled

AMD Overclocking  ↓
SMT Control - Enabled
LN2 Mode 2 - Disabled

AMD CBS  ↓
Global C-state Control - Enabled (Disable if you have locked your CPU freq.)
IOMMU - Disabled ( Needed for Virtual Machines )
CPPC and CPPC Preferred Cores - Disabled (Leave Enabled if you don't have a manual OC)
Core Performance Boost - Disable this if you have a manual cpu overclock + voltage lock. When Setting manual Voltage make sure using the “Override Mode”.

A-XMP - Enabled (Disable if you have manual OC or you use MSI Try It)

GAME BOOST - Disable this if you have a manual cpu overclock + voltage lock.

Advanced DRAM Config ↓
BankGroupSwap - Disabled ( Make sure you don't disable the similar looking setting called “disable bank group swap alt” )
DRAM Latency Enhance - Enabled
Power Down Enable - Disabled
Gear Down Mode - Disabled ( Disable it if you can force T1 )
TSME - Disabled
