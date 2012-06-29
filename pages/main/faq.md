---
layout: default
title: FAQ
heading: FAQ
permalink: /faq.html
---

- ###Recorder is unable to compile the code and giving ClassNotFound/Missing class error###
Some application uses external libraries for development. Bot-bot recrorder will need this libraries while intgrating itself with the app. To fix this issue please paste any dependency jars onto the **_"lib/extra-libs"_** folder of the recorder and rerun the **_"ant"_** command.

- ###Does bot-bot works with an android application apk file?###
Yes. Bot-bot works with Native android application apk files.

- ###Does bot-bot supports Hybrid applications (ex. applications using native and webview both the components)###
Bot-bot runner supports WebViews partially and supports use of search text, asser text present, assert text not present actions on a webview.</br>
Currently recorder does not support WebViews or Hybrid applications.</br>
This will be supported in coming releases.
