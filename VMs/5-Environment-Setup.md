This page describes how to configure your development/build environment on your local map or VM.

<!-- TOC -->

- [Applications and development tools](#applications-and-development-tools)
- [Install and Configure Android Studio](#install-and-configure-android-studio)
- [Package Managers and Packages](#package-managers-and-packages)
- [Configure your Bash Profile](#configure-your-bash-profile)
- [Configuring Android and iOS](#configuring-android-and-ios)
	- [Configuring Android Studio](#configuring-android-studio)
	- [Configuring Xcode](#configuring-xcode)

<!-- /TOC -->

## Applications and development tools
This section lists the tools you need to install:

* **JRE:** <https://www.java.com/en/download/mac_download.jsp>
* **JDK:** <http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html>
* **Xcode:** Download Xcode from the Mac app store

## Install and Configure Android Studio
1. Download Android Studio from <https://developer.android.com/studio/index.html>
1. Launch Android Studio download the Android components.
1. Create a new project.

## Package Managers and Packages
In order to develop and build React Native apps, you need to install the brew and NPM package manages, and the packages described below.

1. Open a terminal window.

1. At the command line install the brew package manager:

   ```/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"```

1. Install the following brew packages:
   * **Node/NPM:** ```brew install node```
   * **Watchman:** ```brew install watchman```

1. Install React Native: ```npm install -g react-native-cli```

## Configure your Bash Profile

1. In an editor, open your bash profile: ```nano ~/.bash_profile```

1. Add the following information
   
		export JAVA_HOME=(/Library/Java/JavaVirtualMachines/jdk1.8.0_121.jdk/Contents/Home)	
		export ANDROID_HOME=(/Users/<user>/Library/Android/sdk)
		export PATH=${PATH}:${ANDROID_HOME}/tools
		export PATH=${PATH}:${ANDROID_HOME}/platform-tools

## Configuring Android and iOS
In order to build Android and iOS, you will need to perform the additional steps described in this section.

### Configuring Android Studio
In order to build the app, you will need to install additional components.

1. Launch Android Studio.

1. In the Welcome dialog, choose **Configure>SDK Manager**

  	![](/img/Screen%20Shot%202017-08-23%20at%2013.32.13.png)   

1. In SDK Manager > SDK Platforms: 
	  * Check **Show Package Details**
	  * For the following Android APIs, make sure only Android SDK Platform is checked: 26,25,24,23
					
		 ![](/img/Screen%20Shot%202017-08-23%20at%2013.33.14.png)  

1. In SDK Manager > SDK Tools: 
	  * Check **Show Package Details**
	  * For the following Android SDK Tools, make sure only Android SDK Platform is checked: 23.0.1-3,24.0.0-3, 25.0.0-3, 26.0.1
						
		![](/img/Screen%20Shot%202017-08-23%20at%2013.33.42.png) 

1. Click **OK** to install the updates.			

### Configuring Xcode
In order to build the app, you will need to perform the tasks described below.

1. Launch Xcode.

1. From the Xcode menu, choose **Preferences**.

	  ![](/img/Screen%20Shot%202017-08-23%20at%2013.59.34.png)

1. In the Preferences dialog, click the **Accounts** tab.

	  ![](/img/Screen%20Shot%202017-08-23%20at%2014.00.08.png) 

1. Click **+** and choose **Apple ID...**
	  
	  ![](/img/Screen%20Shot%202017-08-23%20at%2014.05.34.png) 

1. In the dialog, enter the nrsbrick account credentials.
	  
	  ![](/img/Screen%20Shot%202017-08-23%20at%2014.00.27.png) 

1. Click **Sign in**

1. In the Preferences dialog, click the **Locations** tab

1. From **Command Line Tools**, choose **Xcode 8.3.3**

	  ![](/img/Screen%20Shot%202017-08-22%20at%2016.55.42.png) 

  