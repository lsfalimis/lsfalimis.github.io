---
layout: post
title:  "Clickable URLs in Sublime Text"
description: ""
category: Mac
tags: [Sublime Text]
comments: true
share: true
---

- Install Package Control: ⌃` and copy & paste the code in <https://sublime.wbond.net/installation>

- Install Clickable Urls package: ⌘⇧P, type in 'install' and press ↩, wait for some seconds and a menu will show up, input 'Clickable Urls' and press ↩

- Bind ⌃ left click as the way to click and open URLs in ST3. You can change `control` in the code to any modifier key you like.

{% highlight bash %}
echo '[{ "button": "button1", "modifiers": ["control"], "press_command": "open_url" }]' > ~/Library/Application\ Support/Sublime\ Text\ 3/Packages/User/Default\ \(OSX\).sublime-mousemap
{% endhighlight %}