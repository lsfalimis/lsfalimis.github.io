---
layout: post
title: "Use Hazel to Schedule Single File Transfer"
description: ""
category: Mac
tags: [Hazel, Shell]
comments: true
share: true
---

<figure>
	<img src="http://i.imgur.com/zcp81lu.png" alt="">
</figure>

Here what I want to do is to move the oldest file from folder A to folder B at a specified time every day.

<!--more-->

Simply because of perfectionism of lhunath's [answer](http://stackoverflow.com/questions/937716/how-do-you-send-the-output-of-ls-to-mv/938052#938052) in Stack Overflow, yes, I wasted over an hour trying to do this using `find` command.

[Explainshell.com](http://explainshell.com/explain?cmd=find%20.%20-type%20f%20-exec%20ls%20-s%20%7B%7D%20%5C%3B%20%7C%20sort%20-n%20-r%20%7C%20head.1posix%20-5) is crazy.

After googling, I came up with `gfind * -printf '%p\n' | sort | head -n1` with output `1.txt` [I `touch 1.txt` first, then `touch 2.txt`; `touch` is a bash command that create a new file]. But I couldn't pass `1.txt` output to `mv` command. (`-printf` option is not available in OS X's `find` so I need to `brew install findutils` to install `gfind` where `g-` prefix stands for [GNU](http://en.wikipedia.org/wiki/GNU).)

And later I had `find * -exec ls -t {} | tail -n1 {} \; -exec mv {} ~ \;` with the following output:

{% highlight bash %}
find: -exec: no terminating ";" or "+"
tail: {}: No such file or directory
tail: ;: No such file or directory
tail: -exec: No such file or directory
tail: mv: No such file or directory
tail: {}: No such file or directory
==> /Users/henry <==
tail: ;: No such file or directory
{% endhighlight %}

THIS IS CRAZY!!!

Finally I went back to the method looked down upon by the "professionals".

{% highlight bash %}
mv "`ls -t | tail -n1`" /Users/henry/Desktop/B
{% endhighlight %}

where `-t` means listing in the descending order (for date and time, it means 2014 is before 2013); `tail` to select the last (first/one) item, according to `-n1`, of the list; so `ls -tr | head -n1`, where `-r` means reverse, equals to `ls -t | tail -n1`.

