# Lineage-14.1-Samsung-S2-GT-I9100
Installing lineage-14.1 on Samsung-S2-GT-I9100: based on https://www.reddit.com/r/LineageOS/comments/5wmwpq/how_to_install_lineage_on_i9100/

` sudo apt-get install android-tools-adb android-tools-fastboot heimdall-flash `

### Download mode : Volume Down, Home, and Power key
Extract lineage-14.1-2 archive:

`sudo heimdall flash --repartition --pit I9100_1.5GB-System_6GB-Data_512MB-Preload_by-the.gangster.pit --KERNEL boot.img --RECOVERY twrp-3.1.0-0-i9100.img --no-reboot`

* Select and wipe  "System", "Data", "Cache", and "Dalvik Cache" and other internal/external storages
* Make sure that sdcard exists and format it as ext4.

### Recovery mode : Volume Up, Home, and Power key
Enable sideload in TWRP for each file:
```
adb sideload lineage-14.1-*-nightly-i9100-signed.zip
adb sideload open_gapps-arm-7.1-nano-*.zip
adb sideload addonsu-14.1-arm-signed.zip # if root is needed
```

# Lineage-14.1-Nexus-5

### Fastboot: Volume Down,Volume Up and Power

```
adb reboot bootloader
fastboot oem unlock
fastboot flash recovery twrp-x.x.x-x-hammerhead.img
```
In twrp
```
adb push lineage-14.1-*-hammerhead-signed.zip /sdcard/
adb push open_gapps-arm-7.1-nano-*.zip /sdcard/

```


# Lineage 15.1 on Xiaomi Redmi 2 Pro (Wingtech Redmi 2) 
Model HM2014811, HM 2LTE-CU -  2014811
### Fastboot: Volume Down and Power or adb reboot bootloader
```
sudo fastboot oem device-info
sudo fastboot flash recovery twrp-3.2.2-0-wt88047.img
```
### Recovery mode: Volume Down,Volume Up and Power
Make backups 
Select Wipe and then Advanced Wipe.
Select Cache, System and Data partitions to be wiped and then Swipe to Wipe.
```
adb push  lineage-15.1-20180703-nightly-wt88047-signed.zip /sdcard/
adb push  open_gapps-arm-8.1-pico-20180705.zip  /sdcard/
```


