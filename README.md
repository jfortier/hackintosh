# Hackintosh for El Capitan

### Specs
 - Motherboard: Gigabyte z77x-ud3h
 - Processor: i2700k
 - RAM: DDR3 8G 1600MHz
 - Graphics: MSI GTX 650 1G
 - SSD: Samsung 830
 - HDD:
   - Western Digital Black 640G
   - 2x Western Digital Green 2TB
 - PSU: Antec Modular 630w
 - Audio: Focusrite Scarlett 6i6

### Useful Links
 - http://www.tonymacx86.com/el-capitan-desktop-guides/172672-unibeast-install-os-x-el-capitan-any-supported-intel-based-pc.html (followed pure clover method)
 - http://clover-wiki.zetam.org/Configuration#Config.plist-structure

### Downloads
 - Essentials: http://www.tonymacx86.com/downloads.php?do=file&id=294
 - Clover EFI Bootloader: http://sourceforge.net/projects/cloverefiboot/files/Installer/

## Instructions

**Note** At this point, this is purely from memory I will test the instructions later.

### Creating an OS X Install USB (do this on another mac, I used my macbookpro)

 - Download El Capitan from App Store
 - Use disk utility to format USB stick w/ GUID Journaled w/ name ‘Untitled’
 - Run this to create Install USB
 ```
 sudo /Applications/Install\ OS\ X\ El\ Capitan.app/Contents/Resources/createinstallmedia --volume /Volumes/Untitled --applicationpath /Applications/Install\ OS\ X\ El\ Capitan.app --nointeraction
 ```
 - Install EFI Bootloader to USB Drive
   - Check UEFI Booting only
   - Check Install Clover in the ESP
   - Check Drivers:
     - CsmVideoDxe-64
     - OsxAptioFix2Drv-64






