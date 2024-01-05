# About
This repository keep and maintenance my Opencore EFI for ASRock Z690M PG Riptide/D5.

# Hardware
<table>
       <tr><td>Motherboard</td><td>ASRock Z690M PG Riptide/D5</td></tr>
       <tr><td>CPU</td><td>Intel Core i9 12900KF</td></tr>
       <tr><td>Memory</td><td>Samsung DDR5-4800 32GB x2<br>(M323R4GA3BB0-CQK)</tb></tr>
       <tr><td>dGPU</td><td>AMD Radeon RX 560<br>(ASUS DUAL-RX560-4G)</td></tr>
       <tr><td>Sound</td></td><td>Realtek ALC897</td></tr>
       <tr><td>Ethernet</td><td>Intel Killer E3100G</td></tr>
       <tr><td>Wifi + BT</td><td>N/A (wired connection)</td></tr>
</table>

# What working / Not working
## TL;DR
- Opencore 0.9.7 DEBUG
- macOS Sonoma 14.1.2
- GPU acceleration
- Ethernet
- PCIe / Memory-Slot
- Sleep / Shutdown / Reboot

## Details

Expand the list below. \
The list has copy and edited form  [Hackintosh checklist](https://chriswayg.gitbook.io/opencore-visual-beginners-guide/step-by-step/hackintosh-checklist). See copy source for criteria, etc.

- **Working:** check-mark.
- **Not Working:** bold.
- **Not Tested:** leave as-is.
- **Not applicable:** Strikethrough or delete.

<details><summary>Expand</summary><div>

### Desktop and General

#### OpenCore Booting

* [x] Correct OS choices shown in OpenCore Menu/GUI
* [ ] Keyboard shortcuts working
* [x] NVRAM working
* [x] Security (especially SIP)
<!-- * [ ] FileVault (if used) -->
<!-- * [ ] Windows 10 and/or Linux Multi-Boot -->
* [x] Recovery (macOS) Boot
* [x] Serial Number: You have to generate your own.

#### Display

* [x] Display via HDMI
* [ ] Display via DisplayPort
<!-- * [ ] Display via DVI -->
* [x] Native Resolution
* [x] Refresh rates
* [ ] Multimonitor displays

#### Graphics Acceleration

* [x] dGPU dedicated GPU
<!-- * [ ] iGPU internal GPU
  * In _Terminal_: `gfxutil -f IGPU` or check in _IORegistryExplorer_ -->
* [x] QE/CI (full acceleration requires both Quartz Extreme and Core Image)
* [x] VDA (Video Decode Acceleration framework)
  * Or use `VDADecoderChecker`
* [x] Metal
<!-- * [ ] Intel Quick Sync, H.264 & HEVC (H.265) hardware decoding/encoding
  * _Intel Power Gadget > GFX_ (green line) check while exporting H.264 from FCP-X -->
* [x] dGPU hardware acceleration

#### Audio

* [ ] Audio out
* [x] Audio in
<!-- * [ ] Frontpanel audio connectors -->
* [x] Audio over HDMI
* [x] Audio quality

#### Sleep & Power

* [x] Check Hibernate Mode (desktop `0`, laptop `3`)
* [x] Shutdown (from Apple menu)
* [x] Restart (from Apple menu)
* [x] Manual Sleep (Apple menu -> Sleep) (But it feel take bit longer)
* [ ] **[Press and hold power button for 1.5 seconds](https://support.apple.com/en-us/HT201236), select Sleep**
* [x] Auto Sleep
* [x] Wake by keyboard
* [x] Wake by mouse/trackpad

#### CPU

* [ ] CPU Power Management [Optimizing Power Management](https://dortania.github.io/OpenCore-Post-Install/universal/pm.html#optimizing-power-management)
* [x] Temperatures and stability with 100% CPU

#### Disk

* [ ] NVMe SSD (PCIe Gen3 or Gen4 speeds)
* [ ] SATA SSD
* [ ] TRIM support

#### Sensors

Check with HWMonitorSMC2

* [ ] **CPU**
* [ ] **GPU**
* [ ] **SSD**, **NVMe**, HD
* [ ] **Fans**

#### Keyboard

* [x] Option/Command correctly mapped in macOS
<!-- * [ ] Fn keys working (Audio Volume keys, etc.) -->

#### USB

* [x] USB 2 ports
* [x] USB 2 on USB 3 ports
* [ ] USB 3 and 3.1 ports (check transfer speed during copy)
* [ ] USB Type-C ports
<!-- * [ ] SD Card Reader -->
<!-- * [ ] Camera (Photo Booth, Facetime, Zoom) -->
<!-- * [ ] Fingerprint reader -->

<!-- #### ThunderBolt

* [ ] File transfer
* [ ] Display -->

#### Ethernet

* [x] Gigabit LAN
* [x] 2.5GBase-T (especially on Comet Lake and above boards)
* [ ] ~~10GBase-T (Aquantia with updated firmware)~~

<!-- #### Wifi & Bluetooth

* [ ] Wifi transmission speed (Option Click -> Wifi menu bar icon -> check Tx Rate)
* [ ] Bluetooth devices (trackpad, mouse, keyboard, headset)
* [ ] AirDrop (test with iDevices)
* [ ] AirPlay to Mac (macOS Monterey or later, test with iOS 14 or later devices)
  * tap the AirPlay icon on your Apple device to share videos to your Hackintosh
* [ ] Handoff [System requirements for Continuity](https://support.apple.com/en-us/HT204689) and [Use Continuity](https://support.apple.com/en-us/HT204681) which requires macOS Catalina & iOS 13+
* [ ] [Sidecar](https://support.apple.com/en-us/HT210380) requires macOS Catalina or later and a compatible iPad using iPadOS 13 or later. -->

#### OS Features

* [ ] iMessage, FaceTime, App Store, iTunes Store
* [ ] DRM support

[![CC0](https://i.creativecommons.org/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/) __ I make this checklist available under public domain [(CC0)](https://creativecommons.org/share-your-work/public-domain/cc0/)
</div></details>

# Issues
- USB Mapping (Fix later)
- SMC Plugins
- Fix dGPU has miss-recognized as Radeon Pro 560

# Setup
1. Download EFI files.
2. Edit SMBIOS.
3. Setting UEFI.

# Update log
## Last update
- First boot with macOS 14.1.2 .
- Include AppleALC to fix ALC897.
- Include LucyRTL8125Ethernet to enable 2.5GBit Ethernet by Killer E3100G.
- Include RestrictEvents to
  - Custom CPU name in System Information.
  - Prevent PCI configuration warnings in System Settings on MacPro7,1 platforms.
  - Enable OTA updates.