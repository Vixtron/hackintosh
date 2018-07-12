## My Hackintosh tutorial (works for my system, might not do as well for yours.)

1. Run the VM, find a working tutorial and grab the VMWare image, download the app for macOS from the App Store.
2. Partition your flashdrive using disk utility and use the GUID partition map `diskutil eraseDisk "jhfs+" "USB" "GPTFormat" /dev/diskXsY`
3. Mount your flashrive `diskutil mount diskXsY`
4. Run the following to flash the macOS image to your flashdrive <br />
```bash
$ sudo "/Applications/Install macOS your macos.app/Contents/Resources/createinstallmedia" --volume  /Volumes/USB --applicationpath "/Applications/Install macOS your macos.app" --nointeraction
```
5. Mount the EFI partition `diskutil mount diskXsY`
6. Grab a working Clover bootloader and install it to your EFI partition, use the following configuration <br />
```
Install Clover to the ESP
Drivers64UEFI
    AptioMemoryFix
    Fat-64
```
## Preview
![img2](https://raw.githubusercontent.com/Vixtron/hackintosh/master/clover2.png)

## Installation partition
![img1](https://raw.githubusercontent.com/Vixtron/hackintosh/master/clover1.png)

7. Grab a [FakeSMC](https://github.com/kozlek/HWSensors/releases) binary, run it and extract FakeSMC.kext somewhere and move it to `EFI/Clover/Kexts/Other`
8. Reboot.

## Additional
Get your kexts for network, graphics drivers. <br />
I use Realtek's kext for network, you can grab it here [link](https://bitbucket.org/RehabMan/os-x-realtek-network/downloads/) and extract it to `EFI/Clover/Kexts/Other` on your macOS hard drive/SSD. <br />
Graphics drivers, I use NVIDIA so NVIDIA web drivers will do it for me, you can grab it here [link](https://www.insanelymac.com/forum/topic/324195-nvidia-web-driver-updates-for-macos-high-sierra-update-04252018/) <br />
##### NOTE: some diskutil commands might fail and tell you to try mounting them as readOnly, don't worry, you just have to use sudo in order to mount them as of the new 10.13.6 release.
That's it for now, I will update this repository if there are any future changes.
