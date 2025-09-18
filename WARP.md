# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Repository Overview

This repository contains EFI configurations for running macOS on the Lenovo ThinkPad T14 Gen 1 with Intel i5-10510U (Comet Lake) processor. It includes two complete EFI setups:
- Clover (r5161)
- OpenCore (1.0.5)

## Architecture and Structure

### Key Components

1. Bootloader-specific directories:
   - `Clover/` - Contains Clover r5161 configuration
   - `OpenCore/` - Contains OpenCore 1.0.5 configuration

2. Critical kexts and drivers:
   - Clover uses FakeSMC + sensor plugins
   - OpenCore uses VirtualSMC + SMC plugins
   - Both setups include YogaSMC for ThinkPad-specific features
   - Custom USB mapping configurations
   - Custom SSDTs for EC, battery, and fan sensors

## Development Tasks

### Kext Compilation
To compile custom kexts (requires Xcode 16.3):
```bash
# Clone the required repository
git clone https://github.com/RehabMan/OS-X-FakeSMC-kozlek.git HWSensors-RehabMan-HWSensors-Modify

# Build specific kexts (run one at a time)
xcodebuild -project HWSensors-RehabMan-HWSensors-Modify/HWSensors.xcodeproj -scheme FakeSMC -configuration Release build
xcodebuild -project HWSensors-RehabMan-HWSensors-Modify/HWSensors.xcodeproj -scheme ACPISensors -configuration Release build
xcodebuild -project HWSensors-RehabMan-HWSensors-Modify/HWSensors.xcodeproj -scheme LPCSensors -configuration Release build
xcodebuild -project HWSensors-RehabMan-HWSensors-Modify/HWSensors.xcodeproj -scheme CPUSensors -configuration Release build
```

### Key Paths and Files
- `Clover/` contains Clover bootloader configuration and kexts
- `OpenCore/` contains OpenCore bootloader configuration and kexts
- Root directory contains README.md with hardware specifications and BIOS settings

## Important Notes

1. This repository supports multiple macOS versions:
   - macOS Sequoia
   - macOS Ventura
   - macOS Big Sur

2. Hardware-specific details:
   - Uses MacBookPro16,2 SMBIOS for Clover
   - Uses MacBookPro16,3 SMBIOS for OpenCore
   - Intel UHD Graphics 620 configuration
   - Intel AX210 WiFi (requires AirportItlwm)

3. Development focus:
   - Maintaining compatibility across supported macOS versions
   - Ensuring proper sensor functionality (EC, battery, fans)
   - USB port mapping and Thunderbolt support
   - Hardware feature support (trackpad, battery, EC sensors)