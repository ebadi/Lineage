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
