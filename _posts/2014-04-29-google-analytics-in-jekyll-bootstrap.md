---
layout: post
title: "Google Analytics in Jekyll Bootstrap"
description: ""
modified: 2014-04-29
category: Web
tags: []
comments: true
share: true
---

<!--more-->

It has wasted a newbie like me hours to fix the problem.

The solution is as follows:

- Create a new repository [here](https://github.com/new), fill in Repository name with `GITHUBID.github.io`, and click **Create repository** button
- Download zip file of Jekyll Bootstrap from [here](https://github.com/plusjade/jekyll-bootstrap/) [^1]
- The blog should be able to be opened on <http://GITHUBID.github.io/> after running the code [^2]

{% highlight bash %}
mv jekyll-bootstrap-master.zip /path// &&\
cd /path/ &&\
unzip jekyll-bootstrap-master.zip &&\
mv jekyll-bootstrap-master GITHUBID.github.io &&\
cd GITHUBID.github.io &&\
git init &&\
jekyll build &&\
git add . &&\
git commit -m "first commit" &&\
git remote add origin https://github.com/GITHUBID/GITHUBID.github.io.git &&\
git push -u origin master
{% endhighlight %}

- Create a Google Analytics account by clicking **Access Google Analytics** button
- Go to Admin - Property Settings - at **Default View** choose **All Web Site Data** - Turn on **Enable Demographics and Interest Reports** and **Use enhanced link attribution** - Click **Save** button
- Create google_analytics.html under `_includes/` with the content

{% highlight html %}
<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','//www.google-analytics.com/analytics.js','ga');    

  ga('create', 'TRACKID', 'GITHUBID.github.io');
  ga('require', 'displayfeatures');
  ga('require', 'linkid', 'linkid.js');
  ga('send', 'pageview');    

</script>
{% endhighlight %}

- Open `_includes/themes/twitter/default.html` and change `include JB/analytics` to `include google_analytics.html`
- Run the code under the folder `GITHUBID.github.io`

{% highlight bash %}
jekyll build && git add . && git commit -m "commit" && git push -u origin master
{% endhighlight %}

I also delete some other files but the above steps should be enough to get Google Analytics to work.

[^1]: You can use `curl`
[^2]: `git push -u` [解释](http://www.zhihu.com/question/20019419)
