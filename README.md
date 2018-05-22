## My Hackintosh tutorial (works for my system, might not do as well for yours.)

1. Run the VM, find a working tutorial and grab the VMWare image, download the app for macOS from the App Store.
2. Partition your flashdrive using disk utility and use the GUID partition map. 
3. Mount your flashrive `diskutil mount diskXsY`
4. Run the following to flash the macOS image to your flashdrive `sudo "/Applications/Install macOS your macos.app/Contents/Resources/createinstallmedia" --volume  /Volumes/USB --applicationpath "/Applications/Install macOS your macos.app" --nointeraction`
5. Mount the EFI partition `diskutil mount diskXsY`
6. Grab a working Clover bootloader and install it to your EFI partition, use the following configuration <br />
```
Install Clover for UEFI booting only
Install Clover to the ESP
Drivers64UEFI
    OsxAptioFix2Drv-64
    PartitionDxe-64
```
7. Grab a [FakeSMC](https://github.com/kozlek/HWSensors/releases) binary, run it and extract FakeSMC.kext somewhere and move it to `EFI/Clover/Kexts/Other`
8. Reboot.

## Additional
Get your kexts for network, graphics drivers. <br />
I use Realtek's kext for network, you can grab it here [link](https://bitbucket.org/RehabMan/os-x-realtek-network/downloads/) and extract it to `EFI/Clover/Kexts/Other` on your macOS hard drive/SSD. <br />
Graphics drivers, I use NVIDIA so NVIDIA web drivers will do it for me, you can grab it here [link](https://www.insanelymac.com/forum/topic/324195-nvidia-web-driver-updates-for-macos-high-sierra-update-04252018/) <br />

That's it for now, I will update this repository if there are any future changes.

## Installation preview, Clover bootloader <br />

![img1](https://raw.githubusercontent.com/Vixtron/hackintosh/master/clover1.png)
