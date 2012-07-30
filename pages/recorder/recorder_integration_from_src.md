---
layout: default
title: Recorder
heading: Recorder integration from source
permalink: recorder_integration_from_src.html
---
Recorder can be integrated to an application using following two methodologies.

1. Using an APK
2. Using an Application Source.

----------------

##Recorder integration using the Application source

We suggest using the application source for integrating recorder as this gives the user more flexibity in changing configurations.


###Pre-conditions:

	  	
1. Eclipse is installed on the system.Eclipse can be downloaded from the [link](http://www.eclipse.org/downloads/)
2. AspectJ plugin for eclipse has been installed in eclipse. One of the plugin can found [here](http://www.eclipse.org/ajdt/)
3. Application that needs to be tested source code is available.

-----------
###Installation:

1. Export the bot-bot from git to your local system.
2. Import the source code of the android app that needs to be tested into your eclipse IDE.
3. Right click on the imported android app project -> Configure -> Click on "Convert to AspectJ project".
4. Once your android project is converted to AspectJ, copy the recorder folder from the bot-bot source code to the root of the android project.
5. Select *src* & *aspects* folder under the recorder folder , Right click -> Build-path -> Use as source folder.
6. Copy the "recorder.properties" file from the recorder folder to the "assets" folder of your android source code.
6. After this compile your android app project and run it as an Android application.

**Note:** Hardware key actions will not be recorded when using the application from source option.

----------

