This section describes how to create Mac OS Sierra VMs. 

**Notes:** 
* While in theory it is possible to run the described VMs on Linux or Windows, all the steps described in this and following pages were performed on a MacBook Pro, running MacOS Sierra (10.12.6)
* If you run the VM on non-apple platforms, you may be violating the term's of Apple's licensing agreements. This may not matter for developer and TestFlight builds, but Apple tends to apply stricter standards for apps that will be released via the iOS App Store.
* In order to use this procedure, you must be running VirtualBox 5.1.24 or higher

  ![](./img/Screen%20Shot%202017-08-20%20at%2012.54.50.png)

**To build a virtual machine**

1. Launch VirtualBox.

1. Click **New**

   ![](./img/Screen%20Shot%202017-08-20%20at%2012.54.36.png)

1. In **Name and operating system**:

   * Type a name
   * Set the following options:
     * Type: Mac OS X
     * Version: El Captitan

   ![](./img/Screen%20Shot%202017-08-20%20at%2017.25.37.png)   

1. In **Memory size**, set the VM's memory to 4096 MB.   
 
   ![](./img/Screen%20Shot%202017-08-20%20at%2013.04.34.png)

1. In Hard disk, choose **Create a virtual hard disk now**

   ![](./img/Screen%20Shot%202017-08-20%20at%2013.04.53.png)

1. In **Hard disk**, choose **VDI**

   ![](./img/Screen%20Shot%202017-08-20%20at%2013.05.03.png)   

1. In **File location and size**:
   * Type the drive name
   * Set the drive size to 40GB

   ![](./img/Screen%20Shot%202017-08-20%20at%2013.12.57.png) 
 

