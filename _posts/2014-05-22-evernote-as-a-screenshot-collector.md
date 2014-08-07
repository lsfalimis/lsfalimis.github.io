---
layout: post
title: "Evernote as a Screenshot Collector"
description: "Save Non Retina Size Website Screenshots to Evernote Using Snagit, KM, Hazel and AppleScript: Replacement for Ember?"
category: Mac
tags: [Keyboard Maestro, Share]
comments: true
share: true
---

Retina MacBook Pro was a headache when I stocked screenshots, and Ember seems not able to capture non-retina screenshots. Visual bookmarking also has been a unsolved issue, given Zootool and 爱库 (aiku) were dead, Kippt may not work for some websites and Webbla doesn't support retina (by the way, its version 2 will be available in this summer). More or less, this workaround has solved the above problems, for me.

<a href="#" class="btn btn-success">Gist</a>

<!--more-->

I let Hazel to pass `theFile` to the AppleScript automatically if in the specified folder Hazel finds a file whose extension is png and whose name starts with "webss-" (because I put all screenshots in one place, so a prefix is necessary to separate web screenshots from other screenshots), and after running the AppleScript, Hazel will delete the file.

I let KM to run GUI macro to complete the steps: use shortcuts to activate Snagit to take the screenshot, secondly, activate Snagit main window and save just taken screenshot while prepending "webss-", and lastly, activate Chrome. The whole process, I admit, is slow as it takes 5 seconds, so I can glance the website in the last free 2 seconds; or simply, I can continue my work straight away.

![alt text](http://i.imgur.com/I9UPxql.png "Insert")

---
Update:

I move the action of "activate Google Chrome" from KM to Hazel (as a AppleScript) otherwise it would caused wrong title and URL.