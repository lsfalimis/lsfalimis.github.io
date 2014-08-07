---
layout: post
title: "Use 1Password Like a Pro"
description: "Auto Create a New Password and Auto Fill or Send to iOS"
category: Mac
tags: [Keyboard Maestro, Share]
comments: true
share: true
---

There are two different outputs you can choose: to auto fill new passwords or send new passwords to iOS.

<a href="https://github.com/lsfalimis/Qian-KM-Macros" class="btn">GitHub</a>

<!--more-->

## Auto fill new passwords

1. To use the first macro, you need to open two tabs in Chrome, the first tab would be registration page and another be login page. Place cursor at the input area for username or Email, and then select text in the login page.

2. The macro copies the selected text and pastes into 1Password as the title of the new login password. Then username will be filled in with predefined `USERNAME`. You may have multiple usernames for different purposes; for me, I have one for paid account, another for testing purposes. I can set `⌃0` for another identity.

3. Then, the macro will perform mouse clicking to create a new password. 1Password can be slow, so here I tested many times, the minimum pause for me is one second. (Normally 0.3 second for menu action; for some mouse action, 0.5 is required; one second is needed for webpage loading; anyway, it depends on the network speed and your Mac's speed.) So here the macro fills in the login page's URL.

4. On the next step, the macro `⌘S` the new password, `⌘W` the login page, `⌘V` `USERNAME` (you can append, for example, `@gmail.com` for another macro with an additional modiﬁer key; otherwise, using TextExpander, in my case, to expand `@g` to `@gmail.com` is also handy), and then `⇥`, `⌘V` the newly created password.

![alt text](http://i.imgur.com/y7jPhm3.png "To auto fill")

## Send new passwords to iOS

1. The second macro only requires a selected text for input, I prefer `iOS-` prefix for app password's name, and will not save URL.

2. If you want to save URL, it will be quite easy. Paste the app name, and use shortcut to launch PopClip service, then choose Lucky Link from popup. It will replace the app name as its official website's URL. Sometimes it might not work.

3. Lastly it will press `⇧⌘X` to activate Command-C, and use it to send to the first device. You can tweak it to send to the second device or the third device. For individual cases, you can reduce the time period if your Mac is fast, or increase in the other case.

![alt text](http://i.imgur.com/UGXPgg4.png "Send to iOS")

Enjoy!