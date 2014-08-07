---
layout: post
title: "Custom Search Engines"
description: ""
category: Mac
tags: []
comments: true
share: true
---

Abbr. | Name                    | URL
---   | ---                     | ---
g     | Default                 | `https://www.google.co.uk/#q=%s`
y     | Google (Past Year)      | `https://www.google.co.uk/#q=%s&tbs=qdr:y`
l     | Feel lucky              | `https://www.google.co.uk/#q=%s&btnI`
s     | Search Within a Website | See snippet 1
it    | Open in iTunes Store    | See snippet 2
v     | V2EX                    | `https://www.google.co.uk/#q=site:v2ex.com%2Ft+%s`
a     | alternativeTo           | `http://alternativeto.net/SearchResult.aspx?search=%s`
rss   | Convert to Full RSS     | `http://fullrss.net/analyze/?url=%s`
w     | Wikipedia               | `http://en.wikipedia.org/w/index.php?title=Special:Search&search=%s`
z     | Zhihu                   | `http://www.zhihu.com/search?q=%s&type=question`
{: rules="groups"}

Snippet 1

~~~ javascript
javascript:location=‘http://www.google.com/search?num=100&q=site:'%20+%20escape(location.hostname)%20+%20'%20%S'%20;%20void%200
~~~

Snippet 2

~~~
https://www.google.co.uk/#q=on+the+App+Store+on+iTunes+%s&btnI
~~~
