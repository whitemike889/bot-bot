---
layout: default
title: FAQ
heading: FAQ
permalink: /faq.html
---

- ####Recorder is unable to compile the code and giving ClassNotFound/Missing class error####
Some application uses external libraries for development. Bot-bot recrorder will need this libraries while intgrating itself with the app. To fix this issue please paste any dependency jars onto the **_"lib/extra-libs"_** folder of the recorder and rerun the **_"ant"_** command.

- ####Does bot-bot works with an android application apk file?####
Yes. Bot-bot works with Native android application apk files.

- ####On ANT recorder cmd , I am getting this error where it states the signed apk is not available.?####
JDK 1.7 creates this problem, As of now Android supports only JDK 1.6.

- ####Error Running javac.exe compiler on “ant runner” command?####
This issue is due to the environment variable setting. The JAVA_HOME should point to the JDK instead of jre.

- ####ANT Recorder command fails with exception in Command Prompt?####
In the Recorder.Properties settings file, Set the SERVER_NAME blank.

- ####Recorder Command fails with com.android.dx.util.MutabilityException: immutable instance?####
The Android version should be greater than 3.

- ####I am getting error as table already exist in database in the server console?####
Drop the table in the data base if exists.

- ####How to know database url and password?####
http://localhost:8080/h2/login.jsp  is local database url. Running on port 8080 & the UserName is sa.

- ####Does bot-bot supports Hybrid applications (ex. applications using native and webview both the components)####
Bot-bot runner supports WebViews partially and supports use of search text, asser text present, assert text not present actions on a webview.</br>
Currently recorder does not support WebViews or Hybrid applications.</br>
This will be supported in coming releases.
