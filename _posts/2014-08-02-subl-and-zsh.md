---
layout: post
title: "Subl and Zsh"
description: ""
category: Mac
tags: [Sublime Text]
comments: true
share: true
---

Set up subl in zsh

{% highlight bash %}
# Create a symbolic link (instead of a hard link) by using ln -s
ln -s "/Applications/Sublime Text.app/Contents/SharedSupport/bin/subl" ~/bin/subl
vim ~/.zshrc
{% endhighlight %}

耐心拉到底，到`export PATH="/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin"`这行，在最后括号前加`:$HOME/bin`，然后`:wq`。