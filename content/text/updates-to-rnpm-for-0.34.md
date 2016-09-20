+++
date = "2016-09-20T15:21:04-04:00"
draft = false
title = "Updates to rnpm for 0.34"
description = "With React Native's 0.34 release, we get some neat improvements around the link command. Better logging makes it easier to spot unlinked libraries and we now have pre- and post- unlink hooks."
subscribecopy = "Get In-depth Analysis of New React Native Releases"
categories = ["rnupdates"]
+++

## Better Logging

Sometimes someone adds a library but does not link it. Before React Native 0.34, if you wanted to identify a library that required linking, you would type `react-native link`. You would then be presented with a bunch of text that looked like this:

![Wall of text](https://cloud.githubusercontent.com/assets/997157/17838588/84223264-6796-11e6-81d2-075d30942a69.png)

This is a bummer because you had to read a wall of text just to see if rnpm handled the issue.

Thanks to [Gant Laborde](https://twitter.com/GantLaborde?ref_src=twsrc%5Egoogle%7Ctwcamp%5Eserp%7Ctwgr%5Eauthor), this release speeds up this process by adding a logging level that only logs for previously linked libraries. Now, if you're in this situation, you can identify libraries that haven't been linked "at a glance." It looks a little like this:

![Identify unlinked libs at a glance](https://cloud.githubusercontent.com/assets/997157/17838613/22568c8c-6797-11e6-8e12-c73746ec0eff.png)

## Pre and Post Unlink

`prelink` and `postlink`, in case you didn't know, are [rnpm commands](https://github.com/rnpm/rnpm#commands) that are used to customize a plugin's setup based on a user's input. They are added to a plugin's `package.json` like so:

~~~javascript
"rnpm": {
  "commands": {
    "prelink": "./bin/requestGAToken",
    "postlink": "./bin/linkingSucceeded"
  }
}
~~~

Before 0.34, there wasn't corresponding `preunlink` and `postunlink` commands that could reverse any customizations that were made during the linking phase. Thanks to [Geoff Goe](https://twitter.com/geoffreygoh90), we now have these additional commands to round out our link hook toolset.

Be sure to check out [our upcoming posts](https://codecookbook.co/categories/rnupdates/) on the improvements for React Native version 0.34. If you want those posts delivered to your inbox, sign up on our email list below.
