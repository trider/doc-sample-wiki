This section describes how to upload an app to the iOS app store. The process involves the following steps.

<!-- TOC -->

- [1. Initial Setup](#1-initial-setup)
 - [1.1. Downloading Certificates and Profiles](#11-downloading-certificates-and-profiles)
 - [1.2. Configuring xCode](#12-configuring-xcode)
- [2. Building and Deploying to the App Store](#2-building-and-deploying-to-the-app-store)
 - [2.1. Building the app](#21-building-the-app)
 - [2.2. Validating the App](#22-validating-the-app)
 - [2.3. Uploading the App](#23-uploading-the-app)
- [3. Beta Testing an App with TestFlight](#3-beta-testing-an-app-with-testflight)
 - [3.1. Managing Builds in iTunes Connect](#31-managing-builds-in-itunes-connect)
 - [3.2. Sending Invites to Beta Testers](#32-sending-invites-to-beta-testers)

<!-- /TOC -->

# 1. Initial Setup
This section describes, how to download certificates and profiles so that you can build and deploy the app.

**Note:** You only need to perform this procedure before your create initial build.

## 1.1. Downloading Certificates and Profiles
This section explains how to download the relevant assets from the Apple developer account.

**To download certificates and profiles**

1. In Safari, open the following <https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=891bd3417a7776362562d2197f89480a8547b108fd934911bcbea0110d07f757&path=%2Faccount%2F&rv=1>

1. In the Devloper Page, enter the account credentials

1. In the Developer Page, open **Certificates, Identifiers, & Profiles**

   ![](img/Screen%20Shot%202017-06-08%20at%2012.33.03.png)

1. From Certificates, download the **National Retail Solutions, Inc** certificate.

   ![](./img/Screen%20Shot%202017-06-08%20at%2012.34.18.png)

1. From iOS Provisioning Profiles, download the **Merchant Portal** profiles.

   ![](./img/Screen%20Shot%202017-06-08%20at%2012.34.46.png)

1. On your Mac, locate and double-click on **ios_distribution.cer**.

   ![](./img/Screen%20Shot%202017-06-08%20at%2012.37.39.png)			

1. In the Add Certificates dialog, click **Add**. 

   ![](./img/Screen%20Shot%202017-06-08%20at%2012.35.45.png)	

1. Locate and Double-click	on each of the ***.mobileprovision** files. 

## 1.2. Configuring xCode
Before you can deploy the app, you must perform the following steps.

**To build the app**

1. In xCode, open MerchantPortal, and set **Identity** and **Signing** as shown below. 

   ![](./img/Screen%20Shot%202017-06-08%20at%2012.36.27.png)


1. From the Product menu, choose **Schemes>Edit**

1. In the Dialog, configure the Run scheme as shown below:

	![](./img/Screen%20Shot%202017-06-08%20at%2013.31.56.png)

# 2. Building and Deploying to the App Store
This section describes how to create a build for deployment to the app store.

**Notes** 
* Each time you create a new app store build, you should increment the App's build number. You do not need to increment the Version.
* The app store only supports three level versions, e.g. 0.0.1.
* You should not upload the app while you are connected to the cop
* When  validating or uploading TestFlight builds, disable the **Include app symbols and bitcode** options
  
  ![](./img/Screen%20Shot%202017-06-08%20at%2013.43.59.png)

* Update your info.plist file with the following informations

```
  <key>NSAppTransportSecurity</key>
  <dict>
	<key>NSAllowsArbitraryLoads</key>
	<true/>
	<key>NSExceptionDomains</key>
	<dict>
	 <key>localhost</key>
		<dict>
			<key>NSExceptionAllowsInsecureHTTPLoads</key>
			<true/>
			</dict>
			<key>pos-papi-test.idtretailsolutions.com</key>
			<dict>
				<key>NSExceptionAllowsInsecureHTTPLoads</key>
				<true/>
			</dict>
		</dict>
	</dict>
	<key>NSCameraUsageDescription</key>
	<string>This app needs access to the camera to scan barcodes</string>
	<key>NSLocationWhenInUseUsageDescription</key>
```  
* Check your email app's Junk mail settings. Make sure that iTunes Store notifications are not treated as junk mail.

## 2.1. Building the app

This section describes how to build the app.

**To build the app**

1. In a terminal window, open th ``pos-merchant-mobile`` project directory, and run the following command:			
   ``react-native bundle --entry-file index.ios.js --platform ios --dev false --bundle-output ios/main.jsbundle --assets-dest ios``

	 ![](./img/Screen%20Shot%202017-06-08%20at%2013.08.15.png)

1. In xCode's Product menu, run the following commands:  
    * Build
    * Archive 

## 2.2. Validating the App
Before you upload the app, you should validate it.

**To validate the app**

1. In the Organizer, select the build you want to validate.		
	
	  ![](./img/Screen%20Shot%202017-06-08%20at%2013.14.47.png)	

1. Click **Validate**.

1. In the dialog, select the **National Retail Solutions** profile. 
				
	  ![](./img/Screen%20Shot%202017-06-08%20at%2013.41.35.png)	

1. In the Validate dialog, press **Validate**

   ![](./img/Screen%20Shot%202017-06-08%20at%2013.43.59.png)

1. After validation, press **Done**

   ![](./img/Screen%20Shot%202017-06-08%20at%2013.45.44.png)

## 2.3. Uploading the App
Once the app is validated, you can upload it to the App Store.

**To upload the app**

1. In the Organizer, select the build you want to upload.		
	
	  ![](./img/Screen%20Shot%202017-06-08%20at%2013.14.47.png)	

1. Click **Upload to App Store**

1. In the dialog, select the **National Retail Solutions** profile. 			

	  ![](./img/Screen%20Shot%202017-06-08%20at%2013.41.35.png)	

1. In the dialog, press **Upload**

   ![](./img/Screen%20Shot%202017-06-08%20at%2013.43.59.png)		

1. After upload, press **Done**

   ![](./img/Screen%20Shot%202017-06-08%20at%2014.13.42.png)	

# 3. Beta Testing an App with TestFlight
After the app is successfully uploaded to iTunes Connect, you can make it available for beta testing via TestFlight.

## 3.1. Managing Builds in iTunes Connect
After a build has been processed, use the following steps to release it to beta testers.

**To manage a build in iTunes Connect**

1. In Safari, log into iTunes Connect with the nrsbrick credentials.

   ![](./img/Screen%20Shot%202017-06-08%20at%2016.44.11.png)	

1. In the home page, click **My Apps**

   ![](./img/Screen%20Shot%202017-06-08%20at%2016.47.40.png)	

1. In My Apps, choose **NRSMerchantPortal**.   

   ![](./img/Screen%20Shot%202017-06-08%20at%2016.50.44.png)	

1. Choose **TestFlight**.   

   ![](./img/Screen%20Shot%202017-06-08%20at%2017.07.31.png)

1. Click the uploaded build to set compliance.

   ![](./img/Screen%20Shot%202017-06-08%20at%2017.07.31.png)   

1. In iOS Builds, click **Provide Export Compliance Information**.

   ![](./img/Screen%20Shot%202017-06-08%20at%2017.11.15.png)

1. In Export Compliance Information, choose **No**.   

   ![](./img/Screen%20Shot%202017-06-08%20at%2017.12.43.png)

1. Click **Start Internal Testing**.   

   ![](./img/Screen%20Shot%202017-06-08%20at%2017.13.45.png)   
			
1. Click **Start Internal Testing**.   

   ![](./img/Screen%20Shot%202017-06-08%20at%2017.13.45.png) 

## 3.2. Sending Invites to Beta Testers
When the build is ready, you can invite beta testers to test the build via the TestFlight app.

**To send invites to beta testers**

1. In TestFlight, click on the previous build

   ![](img/Screen%20Shot%202017-06-08%20at%2017.23.50.png) 

1. In iOS Builds, click **Expire Build**.

   ![](./img/Screen%20Shot%202017-06-08%20at%2017.27.36.png)    

1. In the dialog, click **Expire**.

   ![](./img/Screen%20Shot%202017-06-08%20at%2017.28.19.png)    

1. In Build Expired, click **Done**.

   ![](./img/Screen%20Shot%202017-06-08%20at%2017.29.42.png) 