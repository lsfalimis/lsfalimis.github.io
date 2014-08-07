---
layout: post
title:  "Set Up Jekyll on Mac"
description: ""
category: Web
tags: []
comments: true
share: true
---

<!--more-->

I'm one of the **ordinary people** and assume my readers will be ordinary people.

The guide is only for Mac OS X Mavericks and most of the blog posts will be the same.

- Sign up [GitHub](https://github.com/join)

- Create a new repository [here](https://github.com/new). Name the new repo `yourGitHubUsername.github.io`, check “Initialize this repository with a README” and click **Create Repository**.

- Download your repository. Open Terminal and `cd` to the directory you want your blog stay.

~~~ bash
git clone https://github.com/yourGitHubUsername/yourGitHubUsername.github.io.git
~~~

- Install Jekyll.

~~~ bash
xcode-select --install # click Install
\curl -L https://get.rvm.io | bash -s stable --ruby
sudo gem install jekyll # Type your system login password and enter
~~~

- Use Jekyll to produce a new blog.

~~~ bash
jekyll new blog
mv blog/* yourGitHubUsername.github.io.git
cd yourGitHubUsername.github.io.git
jekyll build
jekyll serve
~~~

- Open your browser, type in <http://localhost:4000/> and if you see the webpage, that means so far all is right. End `jekyll serve` by `⌃C`.

- Download GitHub for Mac [here](https://mac.github.com/) and log in your account. Select the repository and click **Commit & Sync**.

- You need to wait for a while and see your blog on `http://yourGitHubUsername.github.io/`