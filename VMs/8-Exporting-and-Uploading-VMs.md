This section describes how to create a VirtualBox appliance (.ova) file. It also describes how to upload it to Amazon's s3 for storage and distribution.

<!-- TOC -->

- [Exporting VMs](#exporting-vms)
- [Uploading VMs to S3](#uploading-vms-to-s3)

<!-- /TOC -->

## Exporting VMs
This section describes how to export and package a VirtualBox VM into a single file.

**To export VMs**

1. In VirtualBox, select a VM.

   ![](/img/Screen%20Shot%202017-08-23%20at%2015.29.37.png)

1. From the File menu, choose **Export Appliance**.

   ![](/img/Screen%20Shot%202017-08-23%20at%2015.34.44.png)   

1. In the dialog, choose **Export**.

   ![](/img/Screen%20Shot%202017-08-23%20at%2015.30.00.png)

## Uploading VMs to S3
This section explains how to upload the exported .ova file to Amazon s3 for storage and distribution.

**To upload VMs to S3**

1. Open a Terminal.

1. At the command line, set the following environmental variables:
   
   ```export AWS_ACCESS_KEY_ID="<redacted>"```

   ```export AWS_SECRET_ACCESS_KEY="<redacted>"```
   
   ```export AWS_DEFAULT_REGION="us-east-1"```  
     
1. Use the following command to upload the file:

   ```aws s3 cp <filepath> s3://tmp-files``` 
