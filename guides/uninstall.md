# Partitioning your POCO X3 Pro

## Files/Tools Needed

Modified TWRP:

| File Name                                       | Android version |
|-------------------------------------------------|-----------------|
| [twrp-3.7.1_vap.img](https://github.com/talveller/POCOX3Pro-Linux-Guides/releases/download/guide_files/twrp-3.7.1_vap.img) | Android 12/12.1/13/14/15 |


- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

- [Mi Flash Tool](https://xiaomiflashtool.com/wp-content/uploads/MiFlash20191206.zip)

- [Latest POCO X3 Pro rom](https://xmfirmwareupdater.com/miui/vayu/stable/V14.0.3.0.TJUMIXM/)
### Notes
>
> [!WARNING]  
> All your data will be erased! Back up now if needed.
>
> Do not run the same command twice.
>
> DO NOT REBOOT YOUR PHONE if you think you made a mistake, ask for help in the Telegram chat no help here.
>
> Do not run all commands at once, execute them in order!

> [!IMPORTANT]
> Make sure you use the MODDED Recovery throughout this whole tutorial as we provide tools to help aid this installation process and make it as easy as possible for you.
>
> If you don't use it and you face any errors, consider it your fault and consider yourself alone if you try asking for support as you have deferred from the main guide.

### Opening CMD as an admin
>
> Download **platform-tools** and extract the folder somewhere, then open CMD as an **administrator**.
>
> It is recommended to keep this window open and use it throughout the entire guide.
>
> Replace `path\to\platform-tools` with the actual path to the platform-tools folder, for example **C:\platform-tools**.

```cmd
cd path\to\platform-tools
```

### Flash the modded recovery
>
> While in fastboot mode, replace `path\to\moddedtwrp.img` with the actual path to the modded recovery image

```cmd
fastboot flash recovery path\to\moddedtwrp.img reboot recovery
```

### Resize partition table
``` cmd
adb shell sgdisk --resize-table 64 /dev/block/sda
```

### Preparing for partitioning
```cmd
adb shell parted /dev/block/sda
```

### Print the current partition table
> Parted will print a list of partitions on your phone. You will see, in this order, the **partition number**, **start value**, **end value**, **partition size**, **filesystem**, and the **partition name**
```cmd
print
```

### Removing userdata
> Replace **$** with the actual number of **esp and linux** (it should be **33 and 34**)
```cmd
rm $
rm $
```

### Recreating userdata
> Replace **150GB** with the actual value you want to allocate to Android. In this example you will have 150GB-11.7GB = **138GB** of usable space
```cmd
mkpart userdata ext4 11.7GB -0MB
```

### Exit parted
```cmd
quit
```

### Formatting data
> Format all data in TWRP, or Android will not boot.
- ( Go to **Wipe** > **Format data** > type **yes** )

- restart the phone to bootloader
```cmd
adb reboot bootloader
```

- 
> then open mi flash tool (XiaoMiFlash.exe) as administrator

<img width="1107" height="710" alt="image" src="https://github.com/user-attachments/assets/298a43c9-4746-4813-b796-e5b38ad7f98d" />

> in <img width="1093" height="71" alt="image" src="https://github.com/user-attachments/assets/fd588165-5af5-40d6-ac57-6f95e1c7cc22" /> click select then chose the path to the rom

> click refresh

> then click clean all

> and one last thing click flash and wait (about 5min)

> and finished
