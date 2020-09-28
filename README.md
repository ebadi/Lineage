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
https://forum.xda-developers.com/redmi-2/how-to/wt88047-redmi-2-resize-partition-t3612933

lineage-17.1-20200926-recovery-wt88047.img
open_gapps-arm-10.0-pico-20200927.1.zip
twrp-3.4.0-0-wt88047.img


fastboot flash recovery twrp-3.4.0-0-wt88047.img
fastboot boot twrp-3.4.0-0-wt88047.img

adb push parted /

adb shell
chmod +x /parted

umount /dev/block/mmcblk0p30
umount /dev/block/mmcblk0p29
umount /dev/block/mmcblk0p28
umount /dev/block/mmcblk0p27
umount /dev/block/mmcblk0p26
umount /dev/block/mmcblk0p25
umount /dev/block/mmcblk0p24
umount /dev/block/mmcblk0p23


/parted /dev/block/mmcblk0
GNU Parted 1.8.8.1.179-aef3
Using /dev/block/mmcblk0
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) p
p
Model: MMC 016G70 (sd/mmc)
Disk /dev/block/mmcblk0: 15.8GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name      Flags
 1      67.1MB  134MB   67.1MB  fat16        modem
 2      134MB   135MB   524kB                sbl1
 3      135MB   135MB   524kB                sbl1bak
 4      135MB   136MB   1049kB               aboot
 5      136MB   137MB   1049kB               abootbak
 6      137MB   138MB   524kB                rpm
 7      138MB   138MB   524kB                rpmbak
 8      138MB   139MB   524kB                tz
 9      139MB   139MB   524kB                tzbak
10      139MB   140MB   524kB                hyp
11      140MB   141MB   524kB                hypbak
12      141MB   142MB   1049kB               pad
13      142MB   143MB   1573kB               modemst1
14      143MB   145MB   1573kB               modemst2
15      145MB   146MB   1049kB               misc
16      146MB   146MB   1024B                fsc
17      146MB   146MB   8192B                ssd
18      146MB   156MB   10.5MB               splash
19      201MB   201MB   32.8kB               DDR
20      201MB   203MB   1573kB               fsg
21      203MB   203MB   16.4kB               sec
22      203MB   237MB   33.6MB               boot
23      237MB   1310MB  1074MB  ext2         system
24      1310MB  1646MB  336MB   ext4         cache
25      1646MB  1679MB  33.6MB  ext4         persist
26      1679MB  1713MB  33.6MB               recovery
27      1745MB  1745MB  524kB                keystore
28      1745MB  1745MB  32.8kB               config
29      1745MB  1812MB  67.1MB               oem
30      1879MB  15.8GB  13.9GB  ext4         userdata

(parted) u
u
Unit?  [compact]? s
s
(parted) p
p
Model: MMC 016G70 (sd/mmc)
Disk /dev/block/mmcblk0: 30777344s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start     End        Size       File system  Name      Flags
 1      131072s   262143s    131072s    fat16        modem
 2      262144s   263167s    1024s                   sbl1
 3      263168s   264191s    1024s                   sbl1bak
 4      264192s   266239s    2048s                   aboot
 5      266240s   268287s    2048s                   abootbak
 6      268288s   269311s    1024s                   rpm
 7      269312s   270335s    1024s                   rpmbak
 8      270336s   271359s    1024s                   tz
 9      271360s   272383s    1024s                   tzbak
10      272384s   273407s    1024s                   hyp
11      273408s   274431s    1024s                   hypbak
12      274432s   276479s    2048s                   pad
13      276480s   279551s    3072s                   modemst1
14      279552s   282623s    3072s                   modemst2
15      282624s   284671s    2048s                   misc
16      284672s   284673s    2s                      fsc
17      284674s   284689s    16s                     ssd
18      284690s   305169s    20480s                  splash
19      393216s   393279s    64s                     DDR
20      393280s   396351s    3072s                   fsg
21      396352s   396383s    32s                     sec
22      396384s   461919s    65536s                  boot
23      461920s   2559071s   2097152s   ext2         system
24      2559072s  3214431s   655360s    ext4         cache
25      3214432s  3279967s   65536s     ext4         persist
26      3279968s  3345503s   65536s                  recovery
27      3407872s  3408895s   1024s                   keystore
28      3408896s  3408959s   64s                     config
29      3408960s  3540031s   131072s                 oem
30      3670016s  30777310s  27107295s  ext4         userdata

(parted)



mkpart system  461920s 3978502s
name 23 system
mkpart cache  3978503s  4633862s
name 24 cache
mkpart persist 4633863s 4699398s
name 25 persist
mkpart recovery 4699399s 4764934s
name 26 recovery
mkpart keystore 4764935s  4765958s
name 27 keystore
mkpart config 4765959s 4766022s
name 28 config
mkpart oem 4766023s 4897094s
name 29 oem
mkpart userdata 4897095s 100%
name 30 userdata




make_ext4fs /dev/block/mmcblk0p23
make_ext4fs /dev/block/mmcblk0p24
make_ext4fs /dev/block/mmcblk0p25
make_ext4fs /dev/block/mmcblk0p30

reboot bootloader

fastboot flash recovery twrp-3.4.0-0-wt88047.img
fastboot flash persist persist.img


fastboot boot twrp-3.4.0-0-wt88047.img

adb pull :

lineage-17.1-20200926-recovery-wt88047.img
open_gapps-arm-10.0-pico-20200927.1.zip

install lineage package in TWRP.

1.Go to TWRP.
2. Wipe
3.Select System.
4.Repair files.
5.Clean 

install open_gapps package

```


