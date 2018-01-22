Before you build the app, follow the steps in described in [1-Build-Processs](https://github.com/coretech/pos-merchant-mobile/wiki/1-Build-Processs)

<!-- TOC -->

- [1. Using Android Studio](#1-using-android-studio)
- [2. Building at the Command Line](#2-building-at-the-command-line)
- [3. Deploying the App to an Android Device](#3-deploying-the-app-to-an-android-device)

<!-- /TOC -->

# 1. Using Android Studio

In order to build the app from Android Studio, use the following procedure.

1. At the command prompt type:

   ``react-native bundle --platform android --dev false --entry-file index.android.js   --bundle-output android/app/src/main/assets/index.android.bundle   --assets-dest android/app/src/main/res/``

1. Launch Android Studio.

1. From the Build menu, choose **Build APK**
 
1. From the Build menu, choose **Generate Signed APK**
   
1. In the Generate Signed APK dialog, click **Next**

   ![](./img/Screen%20Shot%202017-05-29%20at%2012.18.23.png)

1. In Key Store Path, click **Choose Existing** 

   ![](./img/Screen%20Shot%202017-05-29%20at%2013.02.51.png)
	
1. Use the Select Path dialog to locate the ``pos-merchant-app\nrs.key.p12 keystore``

   ![](./img/Screen%20Shot%202017-05-29%20at%2012.19.26.png)

1. Populate the credentials fields with the following information:
	* **Key store password**:``<redacted>``
	* **key alias**: ``<redacted>`` 
	* **key password**:``<redacted>``

1. In the final screen, use the default settings and click **Finish**.
   
   ![](./img/Screen%20Shot%202017-05-29%20at%2012.20.12.png)


# 2. Building at the Command Line

To build from the command line, you must make the following changes to your android environment.

1. Copy ``nrs.key.p12`` 
   * **From:** ``pos-merchant-mobile``
   * **To:**  ``pos-merchant-mobile/android/app``

1. If the file ``pos-merchant-mobile/android/local.properties`` does not exist, create it and add the following:

   ```
   ## This file is automatically generated by Android Studio.
   # Do not modify this file -- YOUR CHANGES WILL BE ERASED!
   #
   # This file must *NOT* be checked into Version Control Systems,
   # as it contains information specific to your local configuration.
   #
   # Location of the SDK. This is only used by Gradle.
   # For customization when using a Version Control System, please read the
   # header note.
   #Thu Jun 01 13:36:42 EEST 2017
   ndk.dir=/Users/<user>/Library/Android/sdk/ndk-bundle
   sdk.dir=/Users/<user>/Library/Android/sdk
   ```

1. In your ``pos-merchant-mobile/android/gradle.properties``, add the following:
   ```
   MYAPP_RELEASE_STORE_FILE=key.p12
   MYAPP_RELEASE_KEY_ALIAS=<redacted>
   MYAPP_RELEASE_STORE_PASSWORD=<redacted>
   MYAPP_RELEASE_KEY_PASSWORD=<redacted>
   ```
1. In ``pos-merchant-mobile/android/app/build.gradle``, add the following to the android section:
    ```
    android {
    ...
    signingConfigs {
     release {
      if (project.hasProperty('MYAPP_RELEASE_STORE_FILE')) {
          storeFile file(MYAPP_RELEASE_STORE_FILE)
          storePassword MYAPP_RELEASE_STORE_PASSWORD
          keyAlias MYAPP_RELEASE_KEY_ALIAS
          keyPassword MYAPP_RELEASE_KEY_PASSWORD
        }
      }
    }
    buildTypes {
      debug {
        minifyEnabled enableProguardInReleaseBuilds
        signingConfig signingConfigs.debug
        proguardFiles getDefaultProguardFile("proguard-android.txt"), "proguard-rules.pro"
      }
      release {
        minifyEnabled enableProguardInReleaseBuilds
        signingConfig signingConfigs.release
        proguardFiles getDefaultProguardFile("proguard-android.txt"), "proguard-rules.pro"
      }
    }
    // applicationVariants are e.g. debug, release
    applicationVariants.all { variant ->
        variant.outputs.each { output ->
          ...
          project.ext { appName = 'MerchantPortal_Android-0.0.2' }
          def newName = output.outputFile.name
          if (newName.contains("release")){
            releaseFindType = ""
            releaseReplaceType = releaseFindType
          }
          if(includeDate){
            def formattedDate = new Date().format('-yyyy-MM-dd_HH-mm-ss')
            releaseReplaceType += formattedDate	
          } 
          newName = newName.replace(releaseFindType, releaseReplaceType)      
          newName = newName.replace("app-", "$project.ext.appName-")
          output.outputFile = new File(output.outputFile.parent, newName) 
        }
      }
   }
    
   ```
1. Change directories to the android folder: ``cd android``

1. To build the app, run one of the following commands:
   * **Debug:**   
     * ``./gradlew assembleDebug``, or 
     * ``./gradlew installDebug -x bundleReleaseJsAndAssets`` 
   * **Release:** 
     * ``./gradlew assembleRelease``, or 
     * ``./gradlew installRelease -x bundleReleaseJsAndAssets`` 

# 3. Deploying the App to an Android Device 
Use these commands to deploy the app to an Android Device using adb:

1. If the app is already installed: ``adb uninstall com.merchantportal`` 

1. To deploy the app to an Android device, : ``adb install -r app/build/outputs/apk/<apk name>.apk``.