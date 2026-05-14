# Kali NetHunter for OnePlus 7T Pro (Oxygen 11.0.5.1)

## Installation
### 1. Unlock Bootloader
1. Enable Developer Options: Settings → About Phone → tap "Build Number" 7 times.
2. Enable OEM Unlocking and USB Debugging.
3. Reboot to fastboot: `adb reboot bootloader`
4. Unlock: `fastboot oem unlock` (confirm on the phone)

### 2. Install TWRP
1. `adb reboot bootloader`
2. `bash fastboot flash recovery twrp-3.6.0_11-0-hotdog.img`
3. `fastboot reboot recovery`
4. `adb sideload twrp-installer-3.6.0_11-0-hotdog.zip`
5. `adb sideload Magisk-v30.7.zip`
6. Reboot to system

### 3. Install Magisk
1. Install the Magisk-v30 app that appears on the phone.
2. Run `adb shell`; `su` – if the system does not give an error, you have obtained root privileges.
3. Reboot the phone and Format /data.
4. `adb sideload Magisk-v30.7.zip`
5. `adb sideload Disable_Dm-Verity_ForceEncrypt_11.02.2020.zip`
6. Reboot to system

### 4. Install Kali NetHunter
1. Install the Magisk-v30 app that appears on the phone.
2. In the Modules menu, install Kali NetHunter (this may take more than 25 minutes).
3. `fastboot reboot recovery`
4. `adb sideload Dora_Nethutner_Kernel.zip`
5. Reboot to system

### 5. Disable OOS Updates and Resolve Battery Drain
1. `su -c pm disable com.oneplus.opbackup` or `resetprop ctl.stop oneplus_brain_service`
2. Create a file named `stop_oneplus_service.sh`.
3. Add the following to the file:

`sh
#!/bin/sh
resetprop ctl.stop oneplus_brain_service`

4. `adb push stop_oneplus_service.sh /sdcard/`
5. `adb shell` ; `su`
6. `mv /sdcard/stop_oneplus_service.sh /data/adb/service.d`
7. `chmod +x /data/adb/service.d/stop_oneplus_service.sh`
8. Reboot system
