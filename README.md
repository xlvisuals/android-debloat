# How to uninstall apps/bloatware from Android phones

The script "uninstall-android-bloat.sh": 
- uninstalls or disables known pre-installed bloatware on Android phones. 
- asks to disable AI or the Google App (if an alternative launcher like Niagara is found).
- prints progress to console and to the file "debloat.log".

Tested on Google Pixel 6a, Google Pixel 9a, and Samsung Galaxy A06 5G.

## 1. Enable developer mode on phone

1. Go to **Settings** \> **About phone**
   1. **Samsung: Settings \> About phone \> Software information**
2. Tap the **Build number** until you see **You are now a developer**!
   - Samsung: The Build number is in 
   - Xiaomi: Tap the **MIUI version** (above ‘Android version’) instead repeatedly
3. Settings \> Additional settings \> **Developer options**
4. Turn on **USB Debugging**
5. If the phone is connected to your computer, you will receive a prompt asking if you want to authorize USB debugging for that computer. Tap **OK** to confirm

## 2. Install **Android SDK Platform Tools** on your computer

### Windows: 

1. Download: [https://dl.google.com/android/repository/platform-tools-latest-windows.zip](https://dl.google.com/android/repository/platform-tools-latest-windows.zip)
2. Unzip into an easily accessible folder such as Downloads/platform-tools
3. Open command Terminal: \[Win\]+\[R\], type cmd, hit \[Enter\]
4. Navigate to this folder, *cd %userprofile%/Downloads/platform-tools*

### macOS:

1. Download: [https://dl.google.com/android/repository/platform-tools-latest-darwin.zip](https://dl.google.com/android/repository/platform-tools-latest-darwin.zip)
2. Unzip into an easily accessible folder such as Downloads/platform-tools
3. Open command Terminal: \[Cmd\]+\[Space\], type Terminal, hit \[Enter\]
4. Navigate to this folder, *cd ~/Downloads/platform-tools*

### Linux:

1. Download: [https://dl.google.com/android/repository/platform-tools-latest-linux.zip](https://dl.google.com/android/repository/platform-tools-latest-linux.zip)
2. Unzip into an easily accessible folder such as Downloads/platform-tools
3. Open command Terminal: \[Ctrl\]+\[Alt\]+\[T\], or open Terminal app from menu
4. Navigate to this folder, *cd ~/Downloads/platform-tools*


## 3. Connect phone to computer using USB

1. Connect your device to your Mac with a compatible USB cable. 
   - If it is the first time connecting after enabling USB Debugging in Developer options, you will receive a prompt asking if you want to authorize USB debugging for that computer. Tap **OK** to confirm
2. Change the USB connection mode to “USB Tethering” mode. 
3. Run the script:
```
chmod +x uninstall-android-bloat.sh
./uninstall-android-bloat.sh
```


## 4. Common adb commands

- To list attached devices:
  - adb devices
- To list installed packages:
  - adb shell cmd package list packages 
- To list disabled packages:
  - adb shell pm list packages -d
- To list android version:
  - adb shell getprop ro.build.version.release
- To disable a package:
  - adb shell pm disable -k --user 0 \<packagename\>
- To enable a package:
  - adb shell pm enable \<packagename\>
- To uninstall a package:
  - adb shell pm uninstall -k --user 0 \<packagename\>
- To reinstall a package:
  - adb shell pm install-existing \<packagename\>
