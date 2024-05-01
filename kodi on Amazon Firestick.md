#setup
# Using adb link
[Download adb link](http://www.jocala.com/adblink.html) and install on Windows.

## Connecting
On Firestick
- Enable ADB Debugging
- Get IP address of Firestick

Open cmd to use ADB link.
Connect to device
```bash
adb connect <ipaddress_of_firestick>
```
On Firestick, you will get a notification to allow or deny ADB debugging from a given device. Allow.

Running following command should list the IP address as `device`
```bash
adb devices

List of devices attached
192.168.29.20:5555      device
```
To disconnect
```bash
adb disconnect
```
## Kodi userdata location
Kodi user data on Firestick is located at 
```bash
adb shell ls /storage/sdcard0/Android/data/org.xbmc.kodi/files/.kodi/userdata
```
## Copying files from local to Kodi
```bash
adb push D:/advancedsettings.xml /storage/sdcard0/Android/data/org.xbmc.kodi/files/.kodi/userdata

adb push D:/somefont.otf /storage/sdcard0/Android/data/org.xbmc.kodi/files/.kodi/media/Fonts
```

# Extras
As part of your file storage, move all extra content to a folder "Extra".

Install Kodi Add-on called "Extras". This will add long-press-context menu item "Extras" for each Movie and TV Show.

Push this [advancedsettings.xml to prevent extras being added to the library](https://kodi.wiki/view/Add-on:Extras#Preventing_Extras_Being_Added_To_Library) to the following location
```bash
/storage/sdcard0/Android/data/org.xbmc.kodi/files/.kodi/userdata
```
# Custom subtitle fonts

Push .ttf or .otf file to 
```bash
/storage/sdcard0/Android/data/org.xbmc.kodi/files/.kodi/media/Fonts
```

# References
[SMB as a source to Kodi](https://kodi.wiki/view/SMB)
[Useful adb commands](https://gist.github.com/Pulimet/5013acf2cd5b28e55036c82c91bd56d8)
[Kodi advancedsettings.xml](https://kodi.wiki/view/Advancedsettings.xml)
[Kodi Extras](https://kodi.wiki/view/Add-on:Extras)
[Kodi data folder](https://kodi.wiki/view/Kodi_data_folder)
[Kodi userdata](https://kodi.wiki/view/Userdata)
[How to Connect ADB and Run Shell Commands on a Fire TV Stick](https://www.aftvnews.com/how-to-connect-to-a-fire-tv-or-fire-tv-stick-via-adb/)
