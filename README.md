# Lenovo ThinkPad T14 Gen 1 – i5-10510U – UHD 620 EFI

This repository contains **two complete EFI folders** for Hackintosh on the Lenovo ThinkPad T14 (1st Gen – Intel i5-10510U – Comet Lake), supporting macOS Ventura, Big Sur, and Sequoia.

---

## ✅ Compatibility

| Feature         | Clover | OpenCore |
|-----------------|--------|----------|
| macOS Sequoia   | ✅     | ✅       |
| Ventura         | ✅     | ✅       |
| Big Sur         | ✅     | ✅       |
| Battery         | ✅     | ✅       |
| Trackpad        | ✅     | ✅       |
| EC Sensors      | ✅     | ✅       |
| USB Mapping     | ✅     | ✅       |
| Thunderbolt     | ✅     | ✅       |

---

## 🧰 Hardware Information

| Item         | Detail                                                    |
|--------------|-----------------------------------------------------------|
| Model        | Lenovo ThinkPad T14 Gen 1                                 |
| Processor    | Intel Core i5-10510U (Comet Lake)                         |
| Graphics     | Intel UHD Graphics 620                                    |
| RAM          | 16 GB DDR4 @ 2666 MHz (dual-channel?)                     |
| SMBIOS       | MacBookPro16,2 (Clover) / MacBookPro16,3 (OpenCore)       |
| SSD          | NVMe 1 TB                                                 |
| Display      | 14″ Full HD IPS (if applicable)                           |
| Bootloader   | Clover r5161 / OpenCore 1.0.5                             |
| Wi-Fi        | Intel AX210 (requires AirportItlwm for support)           |

---

## 📁 Folder Structure

### 🟢 `Clover/`
- Based on Clover r5161
- Includes:
  - FakeSMC + Plugins (ACPISensors, LPCSensors, CPUSensors)
  - YogaSMC.kext
  - Custom SSDTs for EC, battery, and fan sensors
  - USB mapping (USBInjectAll + SSDT-USB)

### 🟣 `OpenCore/`
- Based on OpenCore 1.0.5
- Includes:
  - VirtualSMC + SMCSuperIO, SMCProcessor
  - YogaSMC.kext v2.0.0
  - USBPorts.kext
  - SSDTs compatible with EC sensors (battery and fan)

---

## 🧪 Kext Compilation (Xcode)

To compile the custom kexts:

1. Clone `HWSensors-RehabMan-HWSensors-Modify`
2. Open the project in **Xcode 16.3**
3. Select a scheme: `FakeSMC`, `ACPISensors`, `LPCSensors`, or `CPUSensors`
4. Choose `Release` as build configuration
5. Press `⌘ + B` to build

---

## 🔧 BIOS Settings

**Bold = required**  
*Italic = recommended*

### Config
- *Wake-on-LAN* → Disabled  
- *UEFI Network Stack* → Disabled

### Power
- *Sleep Mode* → Linux

### Thunderbolt
- BIOS Assist Mode → **Disabled**  
- Thunderbolt Security → **Disabled**  
- Thunderbolt Preboot → **Disabled**

### Security
- Fingerprint Predesktop → **Disabled**  
- Secure Boot → **Disabled** (clear all keys if needed)  
- Intel AMT → **Disabled**

### Virtualization
- Kernel DMA Protection → **Disabled**  
- Vt-d → **Disabled** (or enable `DisableIOMapper` quirk)  
- Enhanced Windows Biometrics → **Disabled**

### IO Ports
- Disable unused devices like WWAN, fingerprint  
- Intel SGX → **Disabled**  
- Device Guard → **Disabled**

### Boot
- UEFI/Legacy → **UEFI**  
- CSM → **Disabled**

---
## Credits
## Special thanks // 
- [@hnanoto](https://github.com/hnanoto) – Contributions, patches and tools by Hackintosh and Beyond channel 
- [RehabMan](https://github.com/RehabMan) – SSDTs, FakeSMC and sensor plugins
- [Acidanthera](https://github.com/acidanthera) – OpenCore, VirtualSMC, AirportItlwm
- [@maxpicelli](https://github.com/maxpicelli) – Structure, testing and README
