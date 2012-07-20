---
layout: default
title: Recorder
heading: Installation/Configuration
permalink: recorder_installation.html
---
Recorder can be integrated to an application using following two methodologies.

1. Using an APK
2. Using an Application Source.

----------------
#Using an APK


##Pre-conditions:

1. Android SDK has been installed. More info is available at [link](http://developer.android.com/sdk/installing.html)
2. Apache ant 1.8.3 or higher needs to be installed.[link](http://ant.apache.org/)
3. "apk" file of an app for which automation needs to be done.

-----------
##Installation:

1. Set the "ANDROID_HOME" enviornment variable to the Android SDK installation directory on your system ex. "/opt/softwares/android-sdk-linux"
2. Set the tools and platform-tools folder path to your enviornment PATH. ex. "/opt/softwares/android-sdk-linux/tools" & "/opt/softwares/android-sdk-linux/platform-tools"
3. Open *default.properties* file under the recoder folder and replace the values for the following:
	- *TEST_APK_FILENAME* -> test apk file path.
 	- *ANDROID_VERSION* -> The version of the android platform that you had downloaded using android sdk. This can be found out by going to the platforms under your **Android SDK** installation directory.
	- key.store -> path to your keystore file to be used for signing the andorid application. Once you had installed Androdi SDK and configured a simulator this key store file will be automatically generated in your user home directory under *android* fodler.
	- key.store.password -> password of your keystore
	- key.alias -> Alias for you keystore file
	- key.alias.password -> Password of your keystore alias.
 
	In case you want to use the default keystore file please dont change the above keystore related values in the properties file.

4. Open command prompt and type the command **ant**, this will automatically take your apk file compile it with recorder code, resign it and install it to your emulator or device whichever is running.
5. Once ant build is successful start using the application as you normally do. User actions will be automatically recorded on the server. You can modify and add any new commands required onto the server session. For creating a new session on the server please kill the app from Settings -> Applications and restart the app.
 
**Note: ** Currently *Recorder* will only record user events if the server is running in the same machine where the android simulator is running.

---------
#Using the Application source

We suggest using the application source for integrating recorder as this gives the user more flexibity in changing configurations.


##Pre-conditions:

	  	
1. Eclipse is installed on the system.Eclipse can be downloaded from the [link](http://www.eclipse.org/downloads/)
2. AspectJ plugin for eclipse has been installed in eclipse. One of the plugin can found [here](http://www.eclipse.org/ajdt/)
3. Application that needs to be tested source code is available.

-----------
##Installation:

1. Export the bot-bot from git to your local system.
2. Import the source code of the android app that needs to be tested into your eclipse IDE.
3. Right click on the imported android app project -> Configure -> Click on "Convert to AspectJ project".
4. Once your android project is converted to AspectJ, copy the recorder folder from the bot-bot source code to the root of the android project.
5. Select *src* & *aspects* folder under the recorder folder , Right click -> Build-path -> Use as source folder.
6. Copy the "recorder.properties" file from the recorder folder to the "assets" folder of your android source code.
6. After this compile your android app project and run it as an Android application.


---------------
##Configuration:

You can configure the recording server details for recorder to record its event in the "recorder.properties" file.
Following are the available configuration:

- SERVER_IP -> Recording server IP. Default is 10.0.2.2(localhost). In case the server is not on localhost change it to the server IP. Make sure that the android device is able to connect to the said IP.
- SERVER_PORT -> Port on which the server is running. Default is 8080.
- SESSION_NAME -> Session name that the recroder uses to create the session on the server.
- SERVER_NAME -> Server name . Used in case the server is deployed on a servelet container server like Apache,Jboss. Default its not set and assumes that the user is using the standalone mode of the server.

-----------------

