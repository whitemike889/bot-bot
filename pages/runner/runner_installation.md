---
layout: default
title: Runner
heading: Runner Instalaltion
permalink: runner_installation.html
---
##Pre-conditions:

1. Java jdk neeeds to be installed. More info is available at [link](http://java.com/en/download/index.jsp) 
2. Android SDK has been installed. More info is available at [link](http://developer.android.com/sdk/installing.html)
3. Apache ant 1.8.3 and higher needs to be installed.[link](http://ant.apache.org/)
4. Install one of the android SDK platform using the Android SDK managers.

---------
##Installation:

###For Robotium:

1. Apk file of the application that needs to be tested.
2. Open the resources/default.properties file and change the following values:
	- FRAMEWORK -> "robotium"
	- TESTCASE_FOLDER -> test-case folder name under *testcase* where you have your test-cases in csv format.
	- TEST_APK_FILENAME -> Apk file path of the application that needs to be tested.
	- APP_PACKAGE -> The app package name.
	- DEFAULT_ACTIVITY -> Default lanch activity
 	- ANDROID_VERSION -> The version of the android platform that you had downloaded using android sdk. This can be found out by going to the platforms under your **Android SDK** installation directory.
 	- key.store -> path to your keystore file to be used for signing the andorid application. Once you had installed Androdi SDK and configured a simulator this key store file will be automatically generated in your user home directory under *android* fodler.
	- key.store.password -> password of your keystore
	- key.alias -> Alias for you keystore file
	- key.alias.password -> Password of your keystore alias.

	In case you want to use the default keystore file please dont change the above keystore related values in the properties file.
 

	For finding the values of APP_PACKAGE & DEFAULT_ACTIVITY variables install your application on an emulator and start the application. And then watch the adb logs by typing the command *adb logcat*. And look for the following:

{% highlight ruby %}
"Starting activity: Intent { act=android.intent.action.MAIN cat=android.intent.category.LAUNCHER? flg=0x10200000 cmp=com.example.android/.DefaultLauncherActivity"
{% endhighlight %}


From the above APP_PACKAGE will be *com.example.android* and DEFAULT_ACTIVITY will be *DefaultLauncherActivity*.
	
	
3. Set the "ANDROID_HOME" enviornment variable to the Android SDK installation directory on your system ex. "/opt/softwares/android-sdk-linux"
4. Set the tools and platform-tools folder path to your enviornment PATH. ex. "/opt/softwares/android-sdk-linux/tools" & "/opt/softwares/android-sdk-linux/platform-tools"
5. Place your test-case csv files under a folder inside the *testcases* folder in root of the *runner*.
6. From the command-shell go to the the *bot-bot runner* folder and type the follwing command.
{% highlight ruby %}
ant
{% endhighlight %}
</br>
###For NativeDriver:

1. Export the bot-bot from git to your local system.

2. Import the source code of the android app that needs to be installed into your eclipse IDE.

3. Copy the "server-standalone.jar" from the bot-bot/runner/lib folder to the root of the Android project inside Eclipse IDE and add it to build path.

4. Open the AndroidManifest.xml file of your Android app and paste the following to it:

{% highlight ruby %}
< instrumentation android:targetPackage="{app package name}" android:name="com.google.android.testing.nativedriver.server.ServerInstrumentation" />
< uses-permission android:name="android.permission.INTERNET" /> 
< uses-permission android:name="android.permission.WAKE_LOCK" />
< uses-permission android:name="android.permission.DISABLE_KEYGUARD" />
{% endhighlight %}
</br>
Here the {app package name} needs to be replaced with the name of the package as specified in the mainfest element's package attribute.
</br>
</br>
5. Build and install the android app on to the simulator.
</br>
6. Go to the android sdk installation folder and inside it to platform-tools. Then run the following commands:

{% highlight ruby %}
adb shell am instrument {app_package_name}/com.google.android.testing.nativedriver.server.ServerInstrumentation
{% endhighlight %}
</br>
Here {app_package_name} needs to be replaced with the name of the package as specified in the mainfest element's package attribute.
	
{% highlight ruby %}
adb forward tcp:54129 tcp:54129
{% endhighlight %}
</br>
You can confirm that the instrumentation is started by running adb logcat and looking for a line like this:

{% highlight ruby %}
I/com.google.android.testing.nativedriver.server.ServerInstrumentation(  273): Jetty started on port 54129
{% endhighlight %}
</br>
</br>
7. Package name and initial activity name has to be defined in the BaseClass.java file. (This will be converted to properties file going forward)
</br>8. Run the ant command at the root of the andro_auto_framework directory:

{% highlight ruby %}
ant
{% endhighlight %}
</br>
This will compile your code and execute your test cases. Currently TestNG , Junit & TestNG-xslt report are generated for the test execution.

------------------------------

