---
layout: default
title: Recorder
heading: Recorder Configuration
permalink: recorder_configuration.html
---

##Configuration:

You can configure the recording server details for recorder to record its event in the "recorder.properties" file.
Following are the available configuration:

- SERVER_IP -> Recording server IP. Default is 10.0.2.2(localhost). In case the server is not on localhost change it to the server IP. Make sure that the android device is able to connect to the said IP.
- SERVER_PORT -> Port on which the server is running. Default is 8080.
- SESSION_NAME -> Session name that the recroder uses to create the session on the server.
- SERVER_NAME -> Server name . Used in case the server is deployed on a servelet container server like Apache,Jboss. Default its not set and assumes that the user is using the standalone mode of the server.

-----------------

