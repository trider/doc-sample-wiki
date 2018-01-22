This section describes the build scripts global variables. The scripts are located in the file ```scripts/globals.sh```

The variables can be of the following:
* **Values:** Strings or numbers that indicate literal values. In addition, this file includes compound values that build complex variables, such as file names and paths
* **Flags:** Enable/disable specific actions. Can be set to a boolean value (true/false)   
* **Lists:** Arrays of values, used to perform a list of specific tasks, or to perform specific tasks multiple times

This section describes the following variables:
<!-- TOC -->

- [Git](#git)
- [Help](#help)
- [Project](#project)
- [Config](#config)
- [APIs](#apis)
- [Android](#android)
	- [Flags](#flags)
	- [Values](#values)
- [iOS](#ios)
	- [Flags](#flags-1)
	- [Values](#values-1)
- [Lists](#lists)

<!-- /TOC -->

## Git
GitHub related variables:
* **repo:** path of the project repo
* **repoPath:** path + .git extension
* **buildRepo:** If ```pushToBuildRepo=true```, pushes builds to build repo

## Help
The text displayed by the -h switch.

## Project
Project related variables:
* **branchName:** Project branch to pull from GitHub
* **projectFolder:** The name of the project folder
* **projectName:** Project name, used to generate deliverables, and by app stores
* **projectVersion:** App version number (string)
* **buildNumber:** App build number (int)
* **projectPath:** Compound variable, do not edit
* **releaseName:** Compound variable, do not edit
* **buildDir:** Compound variable, do not edit
* **dirName:** Compound variable, do not edit
* **currProject:** Compound variable, do not edit
* **currRemote:** Compound variable, do not edit

## Config
Configuration specific flags:
* **removeBuilds:** Delete previous build from the builds folder
* **configAppEnv:** Configure build environment
* **storeBuildsOnHost:** Store build source files on build host
* **initBuildProc:** Launch build process
* **updatePackages:** Install NPM packages
* **installNPMPackages:** Install specific package version stored in npmList array
* **finalizeApps:** Performs post build actions 
* **sendMail:** Sends email to address in the mailList array
* **pushToBuildRepo:** Pushes local builds to build repo

## APIs
URLs for different API versions. Not currently in use

## Android

### Flags
Android configuration flags
* **buildAndroid:** Build apk flag
* **includeDate:** Include date in APK name
* **upload2PlayStore:** Upload to Google Play. Not currently in use, requires additional Google Play permissions

### Values
* **releaseType:** Release type, can be debug or release. Not currently in use
* **gradlePath:** Path to ```build.gradle``` file
* **applicationId:** Android/Google play application ID
* **projectRelease:** Compound variable, do not edit
* **apkName:** Compound variable, do not edit
* **apkPath:** Compound variable, do not edit

## iOS
iOS related variables:

### Flags
* **buildiOS:** Build ipa
* **upload2iTunes:** Upload app to iTunes connect. Note that although this feature is fully functional, it is advisable to leave it disabled if you are connected to the internal wired network. It works, but is extremely slow. It can be used over domestic wired/wireless networks.

### Values
* **format:**  The output format of the xcodebuild and altool commands. Currently, set to ```xml```
* **iOSUser:** The user name of the iOS developer account. Current value, ```nrsbrick@gmail.com```
* **iOSPw:** The password for the iOS developer account. Current value, ```Brick1451$```
* **teamID:** Team ID required by Xcode and iTunes. Current value, ```NEQ97ZASL5```
* **bundleID:** Bundle identifier required by Xcode and iTunes. Current value, ```com.nrs.app.merchantportal```
* **method:** The method used to generate a specific app type. Current value, ```app-store```
* **displayName:** The name used to label the app by an iOS device. Current value, ```NRSMerchant```
* **release:** Compound variable, do not edit
* **project:** Compound variable, do not edit
* **build:** Compound variable, do not edit
* **iosRelease:** Compound variable, do not edit
* **ipaPath:** Compound variable, do not edit
* **ipaName:** Compound variable, do not edit

## Lists
**Note:** The version of Bash supported by MacOS (Bash 3) does not support associative arrays. In order to support key/value lists, the ```gradList```and ```envList``` use a workaround that simulates this functionality. In addition, the ```msgList``` local variable in ```build-mobile-apps.sh``` uses the same workaround.
* **npmList:** List of specific NPM packages to install
* **gradleList:** Key/value list that indicates a placeholder, and a related variable. When the script is run the placeholder is replaced by the variables current value
* **iosAddList:** A list of values that are added to the ```exportOptions.plist``` file
* **iosSetList:** A list of values that are updated in the ```info.plist``` file
* **mailList:** A list of email addresses that will receive build notifications
* **envList:** Key/value list of values used to create a ```.env``` file