---
layout: post
title: "Change Jekyll URL When Git Push"
description: "OMG..."
category: Web
tags: [Shell]
comments: true
share: true
---

I just don't get it. What should I supposed to set 'url' in Jekyll's `_config.yml` to `http://localhost:4000` when I'm coding and previewing locally (`jekyll serve --watch`) for the first place?

Luckily, I can have `sed` do this for me :)

{% highlight bash %}
cd ~/GitHub/lsfalimis.github.io && sed -i.bak 's,url: http://localhost:4000,url: http://lsfalimis.github.io,g' _config.yml && git add . -A && git commit -m "update" && git push -u origin master && sed -i.bak 's,url: http://lsfalimis.github.io,url: http://localhost:4000,g' _config.yml
{% endhighlight %}

I declare an alias for this in `~/.zshrc`.