The following pages describe how to build the app for release to the iOS or Google Play app stores.

<!-- TOC -->

- [1. Cloning the Project Repo](#1-cloning-the-project-repo)
- [2. Branching from the Master](#2-branching-from-the-master)
- [3. Configuring the Project](#3-configuring-the-project)

<!-- /TOC -->

# 1. Cloning the Project Repo
This procedure explains how to clone the project repo to a new folder.

**To clone the project repo**

1. Open a terminal window

1. Clone the repo's master branch into a new folder:

   ``git clone https://github.com/coretech/pos-merchant-mobile.git``

   ![](./img/Screen%20Shot%202017-05-30%20at%2013.29.59.png)


# 2. Branching from the Master
If you are working from master, use the following procedure to pull the latest changes and create a new development branch.
 
**To branch from the main branch**

1. In the project folder, pull the latest changes to main.

   ``git pull origin master``

1. Create a new development branch.

   ``git checkout -b [branch name]``

# 3. Configuring the Project
Before you can build the project, you must configure it as described below.

**Note:** If you need to create an app icon, see the [Generating App Icons](https://github.com/coretech/pos-merchant-mobile/wiki/Generating-App-Icons) section   

**To configure the project**

1. If you need to update React Native, run the following commands:
   * ``npm install -g react-native-git-upgrade``
   * ``npm install react-native@latest --save``
   * ``react-native-git-upgrade``
   * ``react-native link``
   * ``RNFB_ANDROID_PERMISSIONS=true react-native link`` 
   
1. Follow the links bellow to build your app for:
   * [Introduction](1-Build-Process-Introduction)
   * [Android](2-Build-Process-Android)
   * [iOS](3-Build-Process-iOS)
   * [iTunes Connect](4-Deploying-to-the-iTunes-Store)

   

