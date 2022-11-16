Disabling iOS OTA Updates – WriteKay 

[Kay Yin](/)
============

Everywhere is within walking distance.

Disabling iOS OTA Updates
=========================

Written on February 9, 2016

This is a three-fold process. One, disabling check and automated download of newOTA updates. Two, removing badge “1” on Settings app. Three, removingdownloaded, but not yet installed OTA packages.

Step One
--------

### Disabling automated checking and download of new OTA updates

You can disable automated downloading of iOS updates by installing the following [tvOS Beta Configuration Profile](#).

> iPhone checks whether an update is available through a special XML document atmesu.apple.com. This configuration profile redirects the check to only look forbeta updates available for the Apple TV. Since your iPhone is not an Apple TV,the redirected catalog check will make your device “believe” iOS is up-to-date.

> The configuration profile is cryptographically signed by Apple (in fact, configuration profile that redirects OTA update catalog through “Internal Settings” will fail to install if it is not), therefore, can be trusted. Other than adding a “Feedback” icon that you can dump into any folder at any time, this configuration profile does not negatively affect your iPhone’s performance or battery life. Don’t worry. It is not possible for your phone to suddenly install tvOS.

> Alternatively, you can also block “mesu.apple.com” through your router settings.However, as you connect your devices to Wi-Fi hotspots that you do not havecontrol of, this would be rendered uneffective.

Step Two
--------

### Removing badge “1” on Settings app

1) You can remove the “1” badge on Settings app icon through backing up your iPhone, then open up the backup in iBackupBot.

2) After that, go to the following directory.

    /System Files/Home Domain/Library/Preferences

Then double click to open the following file:

    com.apple.Preferences.plist

Then locate the following key:

    <key>kBadgedForSoftwareUpdateKey</key>

Then change the value from its initial value…

    <true/>

…into:

    <false/>

Then locate the following key:

    <key>kBadgedForSoftwareUpdateJumpOnceKey</key>

Then change its value from…

    <true/>

…into:

    <false/>

Then click save and close the window.

3) Select the following file

    com.apple.Preferences.plist

Then click Restore in the toolbar. When prompted, untick the third option and only tick “Don’t copy backup” and ”Reboot device after restore (Recommended)”. Then click OK. Your phone will reboot.

4) Navigate to the following folder in iBackupBot:

    /System Files/Home Domain/Library/BackBoard

Then, double click to open the following file:

    applicationState.plist

Then, locate the following key:

    <key>com.apple.Preferences</key>

In the key, find the following entry:

    <key>SBApplicationBadgeKey</key>

Then change the value of the entry from:

    <integer>1</integer>

…into

    <integer>0</integer>

Then click save and close the window.

5) Select applicationState.plist file and click Restore in the toolbar. When prompted, untick the third option and only tick “Don’t copy backup” and ”Reboot device after restore (Recommended)”. Then click OK. Your phone will reboot.

> If everything went well, your phone’s Settings app should no longer be badged. However, it is possible for the changes to not take effect. If that’s the case for you, repeat (5).

Step Three
----------

### Removing downloaded, but not yet installed OTA packages.

You can remove existing downloaded OTA packages at Settings — General — Storage & iCloud Usage.

> Tip: After going through this guide, your iOS device will no longer be bothering you about OTA updates. If you didn’t follow through this guide and don’t mind the nagging and badged Settings icon, keep in mind when iOS prompts you to update, you should choose “Details” rather than “Later”. This is because Apple treats “Later” literally - meaning it will automatically update during midnight.