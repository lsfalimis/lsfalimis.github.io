---
layout: post
title: "Jekyll Bootstrap Clean Setup on Mac"
description: ""
category: Web
tags: []
comments: true
share: true
---

<!--more-->

It's easy to set up new stuff on computers and to forget how to reproduce the same settings in a new one. CRY (Can Reproduce Yourself), for me, is more important than DRY (Don't Repeat Yourself).

The following combines two old posts (I will reposted the delted post about setting up Jekyll): 

> Well, Jekyll Bootstrap is more convenient than Jekyll, though you need to delete a lot of things. However, the amount of things you need to delete for Jekyll Bootstrap may be less than the amount of things you need to add for Jekyll.

>> First of all, I have never study Computer Science, so I treat myself as dummy ass. I might well treat others as dummy asses, so they can reproduce the same things I was talking about.

>>> Anyway, university seems to ask us to write courseworks in a way that treats readers as dummy asses.

Grab a free iTerm2 at `http://www.iterm2.com/#/section/home` and use iTerm2 instead of stock Terminal.app

> I noted it as `xcode-select –install`, but some say `sudo xcode-select –install`, anyway, just type `git` and choose Install. I mean for a new Mac.

~~~ bash
# Install command line developer tools
git
# choose Install
    
# Install oh-my-zsh https://github.com/robbyrussell/oh-my-zsh
curl -L http://install.ohmyz.sh | sh

# Install Homebrew http://brew.sh/#install
ruby -e "$(curl -fsSL https://raw.github.com/Homebrew/homebrew/go/install)"

# You need Homebrew to solve 'Requirements installation failed with status:
#  1' error when installing rvm, and you will need rvm to solve some error
#  about ruby (I didn't jot it down at that time) when installing Jekyll

# Install rvm http://rvm.io/rvm/install

\curl -sSL https://get.rvm.io | bash -s stable --ruby

# error
# /Users/henry/.zshrc:57:export PATH="/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin"
#
# * WARNING: Above files contains `PATH=` with no `$PATH` inside, this can break RVM,
# for details check
# https://github.com/wayneeseguin/rvm/issues/1351#issuecomment-10939525
# to avoid this warning append #PATH.
#
# I should simply edit line 57 of .zshrc; before that, add subl to $PATH;
#  vim is too hard for a dummy ass.
# Create a symbolic link (instead of a hard link) by using ln -s

ln -s "/Applications/Sublime Text.app/Contents/SharedSupport/bin/subl" ~/bin/subl
vim .zshrc

# Press i and go to the edit mode, and then paste:
#  export PATH=$PATH:$HOME/bin
# And it sets up subl
# Press : and type in wq↩ which will save and quit vim.
# Ok, I will not touch vim again.
# However to save time, I can choose replace line 57
#   export PATH="/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin"
#  with:
#   export PATH="$PATH:/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin:$HOME/bin:$HOME/.rvm/bin"
# Actually, 'export PATH="$PATH:$HOME/.rvm/bin" # Add RVM to PATH for scripting'
#  has been added in the last line. We can choose to delete the last line.

# Install jekyll
sudo gem install jekyll

# I cannot figure out git clone in CLI so I wisely choose GitHub GUI Mac app
#  to clone my git to the new OS X.

# cd to the path and type in
rake post title="POST TITLE"
# Happy Blogging!
~~~

Update:
I remember...

iTerm: Agreeing to the Xcode/iOS license requires admin privileges, please re-run as root via `sudo`.

So should open Xcode and agree in the GUI

So should run `sudo xcode-select –install` but when I was redoing this, `-install` and `--install` returned error... Never mind, will check this when I re-clean-install OS X someday.
