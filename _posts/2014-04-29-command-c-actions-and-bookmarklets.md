---
layout: post
title: "Command C Actions and Bookmarklets"
description: ""
category: iOS
tags: []
comments: true
share: true
---

### Drafts

⌘c

{% highlight html %}
command-c://x-callback-url/copyText?text=[[selection]]&deviceIndex=0&x-success={{drafts://}}
{% endhighlight %}

⌘c.o

{% highlight html %}
command-c://x-callback-url/copyAndOpenURL?url=[[clipboard]]&deviceIndex=0&x-success={{drafts://}}
{% endhighlight %}

### Launch

(untitled)

{% highlight html %}
command-c://x-callback-url/copy?deviceIndex=0&x-success={{launchpro://}}
{% endhighlight %}

open

{% highlight html %}
command-c://x-callback-url/copyAndOpenURL?url=[clipboard]&deviceIndex=0&x-success={{launchpro://}}
{% endhighlight %}

### Bookmarklets

o.chrome

{% highlight javascript %}
javascript:location.href=%22googlechrome%22+location.href.substring(4);
{% endhighlight %}

o.clipboard

{% highlight javascript %}
javascript:window.location='command-c://x-callback-url/copy?x-success='+encodeURIComponent(window.location)+'&deviceIndex=0'
{% endhighlight %}
