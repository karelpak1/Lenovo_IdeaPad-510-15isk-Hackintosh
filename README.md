# Lenovo Ideapad 510-15ISK Hackintosh OpenCore macOS Ventura
EFI folder to run latest macOS Ventura version on Lenovo Ideapad 510-15ISK Laptop using OpenCore as bootloader.
## [Dortania's OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide)

## Known problems!
iGPU has only 7MB of video memory

### Original Hardware

Type | Specification | Status
:---------|:---------|:----------
Motherboard | Phoenix BIOS 0XCN45WW | Working
CPU | Intel(R) Core(TM) i5-6200U CPU @ 2.30GHz | Working
Ethernet | Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10) | Working
Wi-Fi & Bluetooth | Intel Dual Band Wireless-AC 3165 Plus Bluetooth | Working
GPU | Intel Skylake GT2 HD Graphics 520 | Working
GPU | Nvidia GeForce 940MX (4GB DDR3) | Disabled
Audio | ????? | Not tested
HDMI | Intel Skylake HDMI | Can't test (HDMI port dead)
Keyboard & Touchpad | Synaptics | Working
Webcam | EasyCamera | Not tested
Card Reader | ????? | Not tested
USB | Sunrise Point-LP USB 3.0 xHCI Controller | Not tested
### Modifications
Type | Status
:--------- |:---------
Patriot Burst SSD 240GB SATA | Working
Western Digital Blue 1TB HDD | Removed
### Used Kexts (!!! ALL ARE DEBUG !!!)

Kext | Info 
:---------|:---------
[Lilu.kext](https://github.com/acidanthera/Lilu/releases) | Arbitrary kext and process patching on macOS.
[AirportItlwm.kext](https://github.com/OpenIntelWireless/itlwm/releases) | Intel Wi-Fi Drivers for macOS.
[IntelBTPatcher.kext](https://github.com/OpenIntelWireless/IntelBluetoothFirmware/releases) | A Lilu base patcher that fix Intel Bluetooth.
[IntelBluetoothFirmware.kext](https://github.com/OpenIntelWireless/IntelBluetoothFirmware/releases) | Intel Bluetooth Drivers for macOS.
[IntelBluetoothInjector.kext](https://github.com/OpenIntelWireless/IntelBluetoothFirmware/releases) | Intel Bluetooth Drivers for macOS (not sure if needed).
[BlueToolFixup.kext](https://github.com/acidanthera/BrcmPatchRAM/releases) | Needed for all non-native Bluetooth devices.
[AppleALC.kext](https://github.com/acidanthera/AppleALC/releases) | Native macOS HD audio for not officially supported codecs.
[RealtekRTL8111.kext](https://github.com/Mieze/RTL8111_driver_for_OS_X/releases) | OS X open source driver for the Realtek RTL8111/8168 family.
[VirtualSMC.kext](https://github.com/acidanthera/VirtualSMC/releases) | SMC emulator layer.
[SMCBatteryManager.kext](https://github.com/acidanthera/VirtualSMC/releases) | Used for measuring battery readouts on laptops.
[SMCProcessor.kext](https://github.com/acidanthera/VirtualSMC/releases) | Used for monitoring CPU temperature.
[VoodooPS2Controller.kext](https://github.com/acidanthera/VoodooPS2/releases) | Legacy support for keyboards (via usb for ex.)
[VoodooPS2Controller.kext](https://github.com/acidanthera/VoodooPS2/releases) | For systems with PS2 keyboards, mice, and trackpads.
[VoodooI2CSynaptics.kext](https://github.com/acidanthera/VoodooPS2/releases) | Frackpad Synaptics
[VoodooI2CELAN.kext](https://github.com/acidanthera/VoodooPS2/releases) | Trackpad ELAN
[WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen/releases) | Various patches necessary for certain ATI/AMD/Intel/Nvidia GPUs.

### Used SSDTs
SSDT | Info
:---------|:---------
[SSDT-PLUG-DRTNIA.aml](https://github.com/dortania/Getting-Started-With-ACPI/blob/master/extra-files/compiled/SSDT-PLUG-DRTNIA.aml) | Used for enabling Apple's XCPM in macOS, allowing for far better CPU power management.
[SSDT-EC-USBX-LAPTOP.aml](https://github.com/dortania/Getting-Started-With-ACPI/blob/master/extra-files/compiled/SSDT-EC-USBX-LAPTOP.aml) | Used for disabling your real Embedded controller and creating a fake one for macOS to play with. USBX portion is used for injection USB power properties missing on Skylake and newer.
[SSDT-PNLF.aml](https://github.com/dortania/Getting-Started-With-ACPI/blob/master/extra-files/compiled/SSDT-PNLF.aml) | Used for controlling the backlight on internal displays such as AIOs and laptops.
