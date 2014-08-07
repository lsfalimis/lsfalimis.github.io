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

~~~
command-c://x-callback-url/copyText?text=[[selection]]&deviceIndex=0&x-success={{drafts://}}
~~~

⌘c.o

~~~
command-c://x-callback-url/copyAndOpenURL?url=[[clipboard]]&deviceIndex=0&x-success={{drafts://}}
~~~

### Launch

(untitled)

~~~
command-c://x-callback-url/copy?deviceIndex=0&x-success={{launchpro://}}
~~~

open

~~~
command-c://x-callback-url/copyAndOpenURL?url=[clipboard]&deviceIndex=0&x-success={{launchpro://}}
~~~

### Bookmarklets

o.chrome

~~~ javascript
javascript:location.href=%22googlechrome%22+location.href.substring(4);
~~~

o.clipboard

~~~ javascript
javascript:window.location='command-c://x-callback-url/copy?x-success='+encodeURIComponent(window.location)+'&deviceIndex=0'
~~~