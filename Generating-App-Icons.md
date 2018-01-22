This page explains how to generate app icons for the home screens of iOS and Android devices. Following is the current app icon. You can download and use this icon in your project.

![icon.png](./img/icon.png)

**To generate app icons**

1. At the command line, install the React Native Toolbox:

   ``npm install -g yo generator-rn-toolbox``

1. If you are installing the toolbox for the first time, install ImageMagick:

   ``brew install imagemagick``
				
1. Download ``icon.png`` to the ``pos-merchant-mobile`` project folder.

	**Note:** If you are creating a new icon, it must be 192x192 pixels.

1. In the ``pos-merchant-mobile`` project folder, run:

   ``yo rn-toolbox:assets --icon ../icon.png``

1. Follow the displayed instructions.

   


    

			