---
layout: post
title: "Launch Mac Actions From iOS"
description: "Log iOS Screenshots in CloudApp and GitHub"
category: iOS
tags: [Hazel]
comments: true
share: true
---

This post will guide you to post last taken iOS screenshot to GitHub.

<!--more--> 

- On OS X:
	- Download and install [Dropbox](https://www.dropbox.com/), [TextExpander (TE)](https://smilesoftware.com/TextExpander/), [Hazel](http://www.noodlesoft.com/hazel.php).
	- Sign in Dropbox and keep it running in the background.
	- Open TE `⌘,` 4th tab, v `Dropbox`, `⌥⌘N` fill in `iOS`, `⌘N` fill in `Logss` and `###%Y-%m-%d %H:%M:%S↩↩![alt text](%clipboard "%e %b %Y %H:%M")↩↩↩`
	- Install [Command-C (Cmd-C)](http://www.commandc.com/) at Mac App Store.
- On iOS:
	- Set up Cmd-C on iOS and move Cmd-C app to the first position in the 'Notification Centre' of iOS.
- On OS X:
	- Open iTerm2, `git` and choose Install.
	- Create a new GitHub repo [here](https://github.com/new).
	- Open iTerm2, create a git locally under Dropbox folder. See the code below.
	- At Chrome's address bar, input `it TextExpander↩` (where `it` is the custom search of `https://www.google.co.uk/#q=on+the+App+Store+on+iTunes+%s&btnI`) and also Dropbox, Cmd-C, Launch Center Pro (LCP) and Drafts, download them in iTunes, and install them on iOS.

{% highlight bash %}
mkdir ~/Dropbox/giti/ &&\
mkdir ~/Dropbox/giti/Qian-iOS-Log/ &&\
cd ~/Dropbox/giti/Qian-iOS-Log/ &&\
touch iPod-touch.md &&\
git init
{% endhighlight %}

- On iOS:
	- Sign in Dropbox.
	- Open TE. At BL(Bottom Left), turn on `Use Dropbox`; you can disable the snippet folders which you don't want to use on iOS.
	- Open Drafts. Tap Share.B(button), **Setting**, turn on **Refresh TextExpander Snippets** and **Expand when typing**; slide to button, turn on **Allow URLs to trigger actions**.
	- Sign in ClouDrop.
- On OS X:
	- Install `⌘C.kmmacros` from [here](https://github.com/lsfalimis/Qian-KM-Macros)
	- Select and `⌃⇧1` (Send to iOS clipboard via Cmd-C on OS X) `launchpro://import?url=cloudrop%3A%2F%2FuploadLatest&title=&description=`
- On iOS:
	- Set up the pasted code in LCP, then set up the second code in LCP: `cloudrop://uploadLatest` 
- On OS X:
	- Select and `⌃⇧1`. See the code below
	- Go to Hazel.prefPane (use [Alfred](http://www.alfredapp.com/)), add folder `~/Dropbox/giti/Qian-iOS-Log/`, then add rule: If `Date Last Modified` `is in the last` `1` `hour` Do `Run shell script`, then tap `i` and paste this `git add . && git commit -m "upload" && git push -u origin master`

{% highlight html %}
drafts://x-callback-url/import_action?type=dropbox&name=logss&path=%2Fgiti%2FQian-iOS-Log%2F&filenametype=2&filename=iPod-touch&ext=md&writetype=2&template=%5B%5Bdraft%5D%5D
{% endhighlight %}

- On iOS:
	- Set up the pasted code in LCP.
	- Snap a screenshot on iOS
	- Open LCP on iOS, **ClouDrop**, wait for upload, tap just uploaded photo, **Copy Link**, **Copy Direct Link**
	- Open Drafts on iOS, type `Logss`, **Share**, tap `logss`
