# MacOS on Teclast F6 Pro

<img align="right" src="/Other/Pics/F6_Pro.png" alt="Teclast F6 Pro macOS Hackintosh OpenCore" width="300">

[![Teclast](https://img.shields.io/badge/Teclast-F6%20PRO-blue)](https://www.teclast.com/en/zt/nb/F6Pro/)
[![MacOS Catalina](https://img.shields.io/badge/Catalina-10.15-red.svg)](https://www.apple.com/)
[![OpenCore](https://img.shields.io/badge/OpenCore-0.7.8-blue)](https://github.com/acidanthera/OpenCorePkg/releases/latest)

## READ THE ENTIRE README.MD BEFORE YOU START

### I am not responsible for any damages you may cause

- I will try my best to keep the repo updated with the latest kexts and OpenCore version.
- This EFI is configured only for Catalina for now.
- With every EFI update you retrieve from here please remember to go through the post install guide.
- Is the first time that i do a hackintosh (all in 5 days, i really need to sleep).

#### Status : WIP

> ### Non-Fuctional

| Feature                              | Status | Dependency          |
| :----------------------------------- | ------ | ------------------- |
| Fingerprint Reader                   | ❌   | Even if it works you cant use it for TouchID. |
| Gyroscope                            | ❌   | Not one Macbook have it. |


> ### Video and Audio

| Feature                              | Status | Dependency          |
| :----------------------------------- | ------ | ------------------- |
| Full Graphics Accleration            | ✅   | `WhateverGreen.kext`  |
| HDMI                                 | ❓   |  Not tested           |
| Audio Recording                      | ✅   | `AppleALC.kext` with Layout ID = 18   |
| Audio Playback                       | ✅   | `AppleALC.kext` with Layout ID = 18   |
| Automatic Headphone Output Switching | ✅   | `AppleALC.kext` with Layout ID = 18   |
| Audio Jack (Can't test microphone Jack because is broken on my laptop) | ✅   | `AppleALC.kext` with Layout ID = 18   |

  
> ### Power, Charge, Sleep and Hibernation

| Feature                              | Status | Dependency          |
| :----------------------------------- | ------ | ------------------- |
| Battery Percentage Indication        | 🟨   | `ECEnabler.kext` little buggy but it works  | 
| sleep mode                           | ✅   |                                    |   
| Battery Life                         | ✅   | Native, comparable to Windows/Linux. |

> ### Input/ Output

| Feature                              | Status | Dependency          |
| :----------------------------------- | ------ | ------------------- |
| WiFi                                 | ✅   | `Itlw.kext`  works with AirportItlwm.kext too but for now is slower |
| Bluetooth                            | ✅   | `IntelBluetoothFirmware.kext`  |
| Card Reader                          | 🟨    | `RealtekCardReader.kext`,  `RealtekCardReaderFriend.kext` it reads SD Cards but fail to write |
| USB 2.0 3.0                          | ✅   | `SSDT-EC-USBX.aml` |

> ### Display, Touchpad, Touchscren, and Keyboard

| Feature                              | Status | Dependency          |
| :----------------------------------- | ------ | ------------------- |
| Brightness Adjustments | ✅  | `WhateverGreen.kext`, `SSDT-PNLF.aml` and `BrightnessKeys.kext`|
| TouchScreen            | ❌  | `VoodooI2C.kext`, `VoodooI2CGoodix.kext` I found the kext but need to edit the SSDT. |
| Trackpad               | 🟨  | `VoodooI2C.kext`, `VoodooI2CHID.kext` sometimes works sometimes doesn't work (when it works, **DON'T open Trackpad settings**) |
| Built-in Keyboard      | ✅  | `VoodooPS2Controller.kext` |
| Multimedia Keys        | ❓  | `BrightnessKeys.kext` |

> ### macOS Continuity

| Feature                              | Status | Dependency          |
| :----------------------------------- | ------ | ------------------- |
| iCloud, iMessage, FaceTime           | ❓   | not tested but i set the Valid SMBIOS  |
| AirDrop                              | ❓   | Not tested  |
| Time Machine                         | ❓   | Not tested  |


Read these before you start:

- [dortania's Hackintosh guides](https://github.com/dortania).
- [dortania's OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide/).
- [dortania's OpenCore Post Install Guide](https://dortania.github.io/OpenCore-Post-Install/).
- [dortania/ Getting Started with ACPI](https://dortania.github.io/Getting-Started-With-ACPI/).
- [dortania/ opencore `multiboot`](https://github.com/dortania/OpenCore-Multiboot).
- [dortania/ `USB map` guide](https://dortania.github.io/OpenCore-Post-Install/usb/).
- [WhateverGreen Intel HD Manual](https://github.com/acidanthera/WhateverGreen/blob/master/Manual/FAQ.IntelHD.en.md).
- `Configuration.pdf` and `Differences.pdf` in each `OpenCore` releases.

</details>

<details>
<summary><strong> REQUIREMENTS </strong></summary>
<br>

- A macOS machine(optional): to create the macOS installer.
- Flash drive, 128GB or more, for the above purpose.  
- [ProperTree](https://github.com/corpnewt/ProperTree) if you need to edit plist files.  
- [MaciASL](https://github.com/acidanthera/MaciASL), for patching ACPI tables and editing ACPI patches.
- [MountEFI](https://github.com/corpnewt/MountEFI) to quickly mount EFI partitions.  
- [IORegistryExplorer](https://developer.apple.com/downloads), for diagnosis.  
- Patience and time, especially if this is your first time Hackintosh-ing.

</details>

<details>
<summary><strong> HARDWARE </strong></summary>
<br>

| Teclast F6 Pro | Hardware                 | 
| :--------------|------------------------- |
| CPU            |  Intel m3-7Y30           | 
| SSD            |  128 GB                  | 
| Display        |  13' IPS (1920x1080)     |  
| WiFi & BT      |  Intel Wireless-AC 3165  |

</details>

<details>
<summary><strong> GETTING STARTED </strong></summary>
<br>

Before you do anything, please familiarize yourself with basic Hackintosh terminologies and the basic Hackintosh process by throughly reading Dortania guides as linked in `REFERENCES`

- Creating a macOS installer: refer to [Dortania's OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/)
- [**README-HARDWARE**](/Other/README_HARDWARE.md): Requirements before installing.
- [**README-OTHERS**](/Other/README_OTHERS.md): for post installation settings and other remarks.

<details>
<summary><strong> CREDITS </strong></summary>
<br>

- [Apple](https://www.apple.com) for macOS.
- [Acidanthera](https://github.com/acidanthera) for all the kexts/utilities that they made.
- [Dortania](https://github.com/dortania) for for the OpenCore Install Guide.

</details>
