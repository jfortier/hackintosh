# Hackintosh for Mojave

### Specs
 - Motherboard: Asus STRIX ROG Z-370-H
 - Processor: Intel i5 8600k
 - RAM: Team Group 8G x 2 DDR4 3000MHz 16-18-38
 - Graphics: Gigabyte AMD RX 580 8GB
 - Drives:
   - 500G Samsung 970 EVO NVMe (OS + Apps)
   - 250G Samsung 830 SSD
   - Western Digital Green 2TB for TimeMachine for the NVMe+SSD
   - 2x Seagate IronWolf 8TB 7200rpm (Plex)
 - PSU: Seasonic 750FM
 - Audio: Focusrite Scarlett 6i6 (1st Gen)
 - 2x 23" LG IPS 231 LCDs

### Tools
 - Clover Configurator: https://mackie100projects.altervista.org/

### 

### Creating an OS X Install USB (do this on another mac, I used my macbook pro)

 - Download Mojave from App Store
 - Use Disk Utility to format USB stick w/ GUID Journaled w/ name ‘USB’
 - Run this to create Install USB
 ```
 sudo /Applications/Install\ OS\ X\ Mojave.app/Contents/Resources/createinstallmedia --volume /Volumes/USB --applicationpath /Applications/Install\ OS\ X\ El\ Mojave.app --nointeraction
 ```
 - Use Clover tool to Install EFI Bootloader to USB Drive
 - Mount the EFI partition it just created using the mount tool in Clover
 - Now copy over the config.plist to "/Volumes/EFI/EFI/Clover" in Finder, or by terminal.
 - In Clover there's a Kext section, as well as an Install Drivers section. When installing be sure to install the following to "Other" on target EFI (USB)
   - Lilu
   - AptioMemoryFix (resolves memory issue)
   - Whatever Green
   - NoVPA
   - USBInjectAll
   - NullCPUPowerManagement (you may have to download this manually but I've found its best to use it when installing OS X only - don't use this kext in your final EFI on your boot drive)
   - IntelMausiEthernet 2.4.0 fixed your network (latest at time)

   Notes:
    - Some of these drivers/kexts may or may not be included in Clover, it changes from time to time. Check https://www.tonymacx86.com/resources/categories/kexts.11/
    - Because I'm using a dedicate audio device with it's own post installation drivers, my configuration does not inlcude an audio kext. 



## BIOS
    Exit → Load Optimized Defaults : Yes
    Advanced \ CPU Configuration → Intel Virtualizaiton Technology: Enabled
    Advanced \ System Agent (SA) Configuration → Vt-d: Disabled
    Advanced \ PCH Configuration → IOAPIC 24-119 Entries: Enabled
    Advanced \ AMP Configuration → Power On By PCI-E/PCI: Enabled
    Advanced \ USB Configuration -> Legacy USB Support: Auto
    Boot → Fast Boot : Disabled
    Boot → Secure Boot → OS Type : Other OS
    Advanced \ System Agent (SA) Configuration \ Graphics Configuration → Primary Display: PEG

## Instructions
 - Boot from USB. If stuck turn on verbosity and the "don't restart on panic" options to help diagnose errors.
 - From Clover Bootloader select Install Mojave on USB
 - Follow on screen instructions, and restart when appropriate.
 - On reboot be sure to use the USB drive as your boot drive – otherwise you won't have the kexts/drivers on your fresh install
 - Select the volume you install OS X to!
 - Complete OS X install on screen instructions (either fresh account, or TimeMachine backup)

## Post Installation
 - If you booted successfully you'll want to create the same EFI volume you did for your boot.
 - Download Clover Configurator and install Clover to your Volume.
 - Copy the config.plist to /Volumes/EFI/EFI/Clover/ like we did with the USB stick
 - Install the following drivers and kexts:
  - Lilu
  - AptioMemoryFix (resolves memory issue)
  - Whatever Green
  - NoVPA
  - USBInjectAll
  - IntelMausiEthernet 2.4.0 fixed your network (latest at time)
  - HibernationFixUp
 - Now eject your USB drive and remove it from the machine.
 - Reboot and ensure you can boot from your target drive.

## Fixing USB so all ports work

 - Use this tool here to generate a kext
 - Mount the EFI of the boot dir using Clover Configurator
 - Copy resulting .kext file over to EFI volumes kext files so its loaded on boot (/Volumes/EFI/EFI/CLOVER/kexts/Other/)
 - Reboot, and all USB devices work, and no more power warnings!

Thanks corpnewt!

https://github.com/corpnewt/USBMap
