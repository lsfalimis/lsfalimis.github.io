---
layout: post
title: "Install MySQL on Mac"
description: ""
category: Mac
tags: []
comments: true
share: true
---

- Download from MySQL official [website](http://dev.mysql.com/downloads/mysql/). Some bugs has been reported by people that use Homebrew to install MySQL.

- Open and install it. There is only one file to install now, not three!

- Edit `~/.zshrc` and add the following lines:

{% highlight bash %}
alias mysql="/usr/local/mysql/bin/mysql"
alias mysqladmin="/usr/local/mysql/bin/mysqladmin"
{% endhighlight %}

- Run `mysqladmin -u root password "yourpassword"` in iTerm2.

- Go to MySQL in System Preference and turn it on.

- Download, install and open [Sequel Pro](http://www.sequelpro.com/). In Host, fill in `127.0.0.1`, username `root` and then password, tap Connect. By the way, the default port is 3306.

- File > Import your .sql file.