<p align="center"><img src="https://github.com/K3V1991/Magisk-Troubleshoot/blob/main/Magisk-Troubleshoot.png" width="300"></a>
<h1 align="center"><b>Magisk Troubleshoot</b></h1>
<br />

* [Magisk - The Magic Mask for Android](https://forum.xda-developers.com/t/magisk-the-magic-mask-for-android.3473445/)
* [Magisk General Support / Discussion](https://forum.xda-developers.com/t/magisk-general-support-discussion.3432382/)
<br />

## Contents:
- [Empty Modules List](#empty-modules-list)
- [Module updated but doesn't show up in the App](#module-updated-but-doesnt-show-up-in-the-app)
- [Error when installing](#error-when-installing)
- [Can't install Modules](#cant-install-modules)
- [Module installed, but don't loading](#module-installed-but-dont-loading)
- [Module installed, but not there after rebooting](#module-installed-but-not-there-after-rebooting)
- [Magisk App Storage Permission](#magisk-app-storage-permission)
- [Process Error](#process-error)
- [Corrupt Zip](#corrupt-zip)
- [Unable to extract Zip](#unable-to-extract-zip)
- [Zip is not a Magisk Module](#zip-is-not-a-magisk-module)
- [Module will be updated at next Reboot](#module-will-be-updated-at-next-reboot)
- [Module causing Issues](#module-causing-issues)
- [Disable, uninstall or delete Modules](#disable-uninstall-or-delete-modules)
- [Safe Mode](#safe-mode)
- [Boot into Android Safe Mode](#boot-into-android-safe-mode)
- [Recovery Module Managers](#recovery-module-managers)
- [Logs](#logs)
<br />
<br />

## Empty Modules List:
If the List of Modules in the Magisk App is empty, clear the Repo Cache in the App Settings and reload the Modules List (the small Icon in the top right Corner of the Modules Window)
<br />
<br />

## Module updated but doesn't show up in the App:
If it seems like a Module has been updated, but it doesn't show up as an Update, there's nothing wrong. <br />
The Date will change and the Module will move to the Top of the Modules List whenever there is any kind of Edit to the Module's Repo on GitHub.
<br />
<br />

## Error when installing:
Try flashing the Zip through Recovery. <br />
If this also fails, save the Recovery Log and post in the Support Thread together with your App Install Log.
<br />
<br />

## Can't install Modules:
If there's an Error installing a Module or the Module seems to install fine but doesn't show up as installed after a reboot.

* Download Error:
Usually this is caused by having a Custom Hosts File, or similar, that is blocking the CDN used by the App.

* Outdated Template:
Magisk Modules Templates used to have a Version Number, but now all Installation Logic is centralised to the Magisk Module Installation Script.
If the Module you are trying to install has a minMagisk Entry in the module.prop File it is very likely that it is too old to be able to install on a recent Version of Magisk.
<br />

## Module installed, but don't loading:
Make sure you haven't disabled Modules by running your Device in "[Safe Mode](#safe-mode)". <br />
Doing this disables all Modules and MagiskHide. <br />
If you have not done this and your Modules are all enabled, there's likely something wrong with your Magisk Installation. <br />
Post Details and Logs in the Support Thread.
<br />
<br />

## Module installed, but not there after rebooting:
Often caused by the Module using an outdated Module Template. See "Outdated Template".
<br />
<br />

## Magisk App Storage Permission:
If the App does not have Storage Permissions there will be Issues with Module Installation. <br />
It should automatically ask for Permission when needed, but if this doesn't work, give the Permission manually.
<br />
<br />

## Process Error:
If there's a "process error" when installing a Module it is usually caused by the App not having Storage Permission. See above. <br />
It might also be fixed by clearing Data for the App.
<br />
<br />

## Corrupt Zip:
Make sure that there's nothing wrong with the Zip File (corrupt, etc.). <br />
Try re-downloading the Zip.
<br />
<br />

## Unable to extract Zip:
If you get an Error stating "Unable to extract zip" when installing a Module it might just mean that the Zip has been packaged wrongly. <br />
Try using a different Program to create the Zip. 
<br />
<br />

## Zip is not a Magisk Module:
If the Error states that it's not a Magisk Zip or invalid Zip in TWRP, the Zip is not packaged correctly. <br />
Open up the Zip and you'll likely see a Folder (named something like <NameOfModule>-master or similar). <br />
Take all the Contents of that Folder and repack it to the Root of the Zip and try flashing it again. <br />
It might also be that you or whoever made the Module forgot to add the Line "#MAGISK" to the updater-script File.
<br />
<br />

## Module will be updated at next Reboot:
If you install a Module and after Reboot it doesn't work or it works but there's a Message in the Magisk App Modules Section that states "module will be updated at next reboot", try this:

* If the Module works, just navigate to the Module Folder under ```/data/adb/modules``` and delete the "update" File. <br />
* If it keeps happening when installing Modules post the Installation Log, Magisk Log and possibly a Logcat from the Installation in the Support Thread. <br />
* If the Module doesn't work and hasn't installed properly. Navigate to ```/data/adb/modules```, delete the Module Folder and try again.
<br />

## Module causing Issues:
If you have a working Magisk Installation, but a Module causes Magisk, Magisk App or your Device to not function properly (Bootloop, Loss of Root, etc.), see below.
<br />
<br />

## Disable, uninstall or delete Modules: 
Since Magisk v19.4, there's an ADB Command that can be used to uninstall all Modules on your Device

1. Connect your Device up to a Computer (or other Device you can run ADB from) and execute the following Command: <br />
```adb wait-for-device shell magisk --remove-modules```
2. Restart your Device and as soon as ADB is available the Command will activate, the Modules will be removed and the Device will reboot. <br />
**Note:** If you do not have USB Debugging enabled ADB won't work and you'll need to use Safe Mode instead.

* Navigate to the Module's Directory under ```/data/adb/modules/``` and rename any File in there to "remove" or "disable"

* In Terminal you can use the touch Command: ```touch /data/adb/modules/<module folder>/remove``` or ```/data/adb/modules/<module folder>/disable```, depending on your Preference <br />
**Note:** If you create the "remove" or "disable" Files, Magisk will take Care of removing or disabling the Module on the next Reboot.

* Simply delete the Module's Folder under ```/data/adb/modules```. This is the last Resort since it won't run any uninstall Script that the Module might use
<br />

## Safe Mode:
From Magisk v21, Core Only Mode has been replaced with Safe Mode. <br />
Booting your Device into Android Safe Mode will disable all Modules and also disable MagiskHide. <br />
Once you reboot back to Normal Android the Modules will remain disabled and you can manage them manually to find and uninstall the Module that is causing Issues.
<br />
<br />

## Boot into Android Safe Mode:
There should be a Button Combination available to activate Safe Mode. <br />
Usually it is something like holding the "Power Button" until the OEM Splash Screen shows and then switching to holding "Volume down" until your Device boots into Safe Mode. <br />
If you cannot get the Button Combination working, you could also disable Magisk completely by flashing the Stock Boot Image to your Device. 
<br />
<br />

## Recovery Module Managers:
There are also a few different Module Managers for Custom Recoverys available (take a look over at [XDA](https://forum.xda-developers.com/)). <br />
These might make it easier for you to manage any installed Modules when you can't boot your Device.
<br />
<br />

## Logs:
If an Error occurs when installing a Module, save the Install Log by clicking on the "Disk Icon" Button. <br />
