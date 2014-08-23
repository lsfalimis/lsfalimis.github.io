---
layout: post
title: "Install mysql-python on Mavericks"
description: ""
category: Mac
tags: [Python]
comments: true
share: true
---

{% highlight bash %}
sudo pip install mysql-python
# EnvironmentError: mysql_config not found
{% endhighlight %}

I need to add `/usr/local/mysql/bin` to `$PATH`, so in terminal I `zshconfig`, find `export PATH="` and add `/usr/local/mysql/bin`. Now it becomes this,

{% highlight bash %}
export PATH="/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin:$HOME/bin:/usr/texbin:/usr/local/mysql/bin"
{% endhighlight %}

and `sudo pip install mysql-python` works.

Then, when I try to use `MySQLdb` to connect MySQL, in terminal I get `Library not loaded: libmysqlclient.18.dylib`. To solve this, run the following in terminal,

{% highlight bash %}
sudo ln -s /usr/local/mysql/lib/libmysqlclient.18.dylib /usr/lib/libmysqlclient.18.dylib
{% endhighlight %}


