# Updating-LOS-with-micro-g-and-magisk
A short guide, on how to update Lineage os with micro-g and magisk installed.

When updating my phone trough the built in updater I was getting error-21 about a failed signature verification. So this is my work around in case anyone is experiencing the same problem.

## Setup

You must have adb installed. Developer options and usb debugging eneabled. Here's a guide on how to do that: https://www.xda-developers.com/install-adb-windows-macos-linux/ , altho you probaby already have done this, since you have magisk.

## 1. Download the LOS packages

For the os package, you can download it 2 ways:
### Option 1. Download it on from the updator on your phone
Simply navigate to settings/system/System_updates, **download** the latest update and **export it**. Then connect your phone to your computer. A message will pop up from Android-System Saying something like "Charging this device via USB, tap for more options". Press the message and select **File Transfer**. Then, on your computer, navigate to where the update is located and transfer it to the computer. 

This method is nice, since you don't have to worry about downloading the correct package that's compatible with your phone. But it is abit of a hasle. 

### Option 2. Download it from the source
Navigate to LOS for micro-g website https://download.lineage.microg.org/ and select your device. Sort files by size, so the biggest files are up top. You only need to download the system package, which should be ~1gb, it will be named lineage-{*version*}-{*date*}-microG-{*device*}.zip. Download the latest one.

## 2. Download the magisk package
When you update your system you need to reflash the magisk package to keep root. Download the latest release (not pre-relase) of the magisk apk from https://github.com/topjohnwu/Magisk/releases . Put it in the same folder with the LOS package. Rename the magisk apk to a zip, e.g. app-release.apk -> app-release.zip .

## 3. Sideload the packages.
Connect your phone to your computer with a quality cable. Open your terminal and check if adb is working. You can do that by typing
```
adb devices
```
This command should output one device. Your phone may ask you to allow the adb connection. 

### Reboot into revocery
```
adb reboot recovery
```

In the recovery navigate to **Apply update** and **Apply from ADB**.

### Sideload the LOS package
```
adb sideload <path-to-LOS>.zip
```
It will say that the key signature is invalid and ask you if you want to continue anyways, press yes.

If the sideload finished succesfully, don't reboot yet, but again navigate to **Apply from ADB**.

### Sideload the magisk package
```
adb sideload <path-to-magisk>.zip
```
After this you can reboot. The startup may take a little longer.

Navigate to the magisk app. It may promt you to do some stuff. Follow the instructions there. That's it.
Here's a link with more detailed info: https://magiskmodule.gitlab.io/proguide/update-lineageos-adb-sideload/

