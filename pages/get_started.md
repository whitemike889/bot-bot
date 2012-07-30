---
layout: default
title: Getting Started
heading: Get Started with bot-bot
---
##Pre-conditions:

1. Java jdk neeeds to be installed. More info is available at [link](http://java.com/en/download/index.jsp) 
2. Android SDK has been installed. More info is available at [link](http://developer.android.com/sdk/installing.html)
3. Apache ant 1.8.3 and higher needs to be installed.[link](http://ant.apache.org/)
4. Install one of the android SDK platform using the Android SDK managers(preferably Android 4.0.X for running the tests).And create a emulator using the said SDK.
5. Set the "ANDROID_HOME" enviornment variable to the Android SDK installation directory on your system ex. "/opt/softwares/android-sdk-linux"
6. Set the tools and platform-tools folder path under android-sdk directory to your enviornment PATH. ex. "/opt/softwares/android-sdk-linux/tools" & "/opt/softwares/android-sdk-linux/platform-tools"

---------
##Recording tests

There are mainly two steps involoved in recording user actions on an android apk. 

1. Start the recording server
2. Integrate the recorder onto the app under test.

####1. Start the recording server
Bot-bot needs a server to record user actions as tests. To start the bot-bot server go to the root directory of the downloaded version of bot-bot using cmd prompt(or terminal in case of linux) and type 

{% highlight ruby %}
ant server
{% endhighlight %}

</br>
This will start the bot-bot server and you can verify it by opening the URl **"http://localhost:8080/index.html"** on a browser.

####2. Integrate the recorder to the app.

Bot-bot already comes with an opensource application wordpress.apk using which you can get a feel of bot-bot recording feature.
So in default.properties set your android version and other settings if required(Please check [configuration](#configuration) for more info). Once done open a new cmd prompt(or terminal in case of linux), go to the root folder of downloaded bot-bot release and type the following:
 
{% highlight ruby %}
ant recorder
{% endhighlight %}

</br>
Once the ant build is successful and the application is installed, you can start the application in your emulator and start using it. All your actions will be recorded and will reflect at server on URl **"http://localhost:8080/index.html"**.

--------------

##Running tests

Bot-bot comes with some sample test cases for the sample app **wordpress.apk** provided along with it. To run these test cases just open the wordpress app earlier installed and then login with a valid username & password of an account in wordpress(preferably a dummy account.A dummy account credentials is not provided as part of the test due to security reasons). Once logged-in try running these tests by going to the root folder of downloaded bot-bot release from command prompt and type the following:

{% highlight ruby %}
ant runner
{% endhighlight %}
</br>
This will install the test app to simulator after resigning and and then starts running your test cases. You can see the test execution on the emulator.
At the end of the test execution bot-bot will create junit and testng reports with pass and fail results.

**Note:** Cases for wordpress.apk are written assuming that user has already logged in before running the cases. Hence all cases start from home screen and not from log in screen. If all the test cases fail because of homescreen not visible, just log in with a wordpress account and then run the tests. Now your wordpress wil not ask you credentials but will start with home screen and all test cases will start passing.

------------
##Integrating your own app with bot-bot recorder/runner

To integrate/use your own app with bot-bot change the following configurations:
</br>
###For recorder
Once you had used bot-bot with the test apk provided just replace the path of your test apk with the sample apk under property **TEST_APK_FILENAME** inside **default.properties** file present under the root of the downloaded bot-bot folder.

###For Runner
For integrating your app with bot-bot please modify the _APP_PACKAGE_, _DEFAULT_ACTIVITY_, _TESTCASE_FOLDER_, _TEST_APK_FILENAME_ sections under the **default.properties** file under root of the downloaded bot-bot.For more info about the configuration sections [click here](#configuration)


----------------
##Configuration<a name="configuration"> </a>

Following are the configuration parameters menntioned in the **default.properties** at the root of the release folder:

- **APP_PACKAGE** -> The app package name.
- **DEFAULT_ACTIVITY** -> Default launch activity
- **FRAMEWORK** -> "robotium"
- **TESTCASE_FOLDER** -> test-case folder name under *testcase* where you have your test-cases in csv format.
- **TEST_APK_FILENAME** -> Apk file path of the application that needs to be tested.
- **ANDROID_VERSION** -> The version of the android platform that you had downloaded using android sdk. This can be found out by going to the platforms under your **Android SDK** installation directory.
</br></br>
- **key.store** -> path to your keystore file to be used for signing the andorid application. Once you had installed Androdi SDK and configured a simulator this key store file will be automatically generated in your user home directory under *android* folder.
- **key.store.password** -> password of your keystore
- **key.alias** -> Alias for you keystore file
- **key.alias.password** -> Password of your keystore alias.

In case you want to use the default keystore file please dont change the above keystore related values in the properties file.
</br></br>
For finding the values of **APP_PACKAGE** & **DEFAULT_ACTIVITY** variables install your application on an emulator and start the application. And then watch the adb logs by typing the command **adb logcat**. And look for the following:

{% highlight ruby %}
"Starting activity: Intent { act=android.intent.action.MAIN cat=android.intent.category.LAUNCHER? flg=0x10200000 cmp=com.example.android/.DefaultLauncherActivity"
{% endhighlight %}
</br>
From the above APP_PACKAGE will be *com.example.android* and DEFAULT_ACTIVITY will be *DefaultLauncherActivity*.

---------------



 


