---
layout: post
title: "Mac Shortcut Setup"
description: "My No-Programmer Window Management and Keyboard Shortcuts Settings"
category: Mac
tags: [Share]
comments: true
share: true
---

<figure>
	<a href="http://i.imgur.com/FcxaTeV.png"><img src="http://i.imgur.com/FcxaTeV.png" alt=""></a>
	<figcaption>Mac Shortcut Mindmap</figcaption>
</figure>

## Contents
{:.no_toc}

* 
{:toc}

<!--more-->

### Notes

- KM cannot move a window and the mouse to the other display.
- Moom moves windows in a way better than other apps but it's slow and you change how the snapping area looks like (I actually don't like the one of Moom). So windows snapping is handed over to BetterSnapTool.
- I also also tried Amethyst ([website](http://ianyh.com/amethyst/), [GitHub](https://github.com/ianyh/Amethyst)) which is similar to [xmonad](http://xmonad.org/) and [xnomad](https://github.com/fjolnir/xnomad) but written in pure Objective-C. However given the fact many OS apps has set minimum window size and you can minimise them further, so if work on big screens I will definitely try this again but now I have a 15" retina MacBook Pro and a 24" Dell U2412M before me, so it's not hard to stay away from tiling window managers.


### BetterSnapTool

Oneside Modifier Key | Other Key | Function
---                  | ---       | ---
⌘r                   | /         | Full Screen
                     | ↑         | Top Half
                     | ↓         | Bottom Half
                     | ←         | Left Half
                     | →         | Right Half
⇧r                   | /         | Center
                     | ↑         | Top Left Quarter
                     | →         | Top Right Quarter
                     | ←         | Bottom Left Quarter
                     | ←         | Bottom Right Quarter
⌥l                   | -         | Move to Top Left Without Resizing
                     | =         | Move to Top Right Without Resizing
⌃l                   | `         | Move to Next Monitor
{: rules="groups"}


### Remapping keys

Left `⇧`, `⌥`, `⌘` are all given a key value by PCKeyboardHack (see the table as follows) and mapped to a new key combo of right modifier key (that is `⇧l`, `⌃l`, `⌥l` and `⌘l`) by KeyRemap4MacBook ([gist](https://gist.github.com/lsfalimis/55b776c1f69d678b22fa) I use two **new** keys, Caps Lock as Hyper Key which equals to `⌃⌥⇧⌘`, and `⌥r` as the key of `Fn` combos; some people set Hyper Key in Alfred... I did it within KM :) ). When single left modifier key is pressed, it will act as the new key; when a combo of a left modifier key and another other key are pressed, it will act as the key combo. By the way, under `System Preferences` > `Keyboard` > `Shortcuts` tab > `Input Sources`, I set `Select the previous input source` to `F18` i.e. `⇧R`; I open Eudic, then `⌘,` at `快捷键` tab, set `激活 Light Peek` to `⌘r` i.e. `F17`. At last, other key shortcuts are in Alfred 2.app, the majority are in Keyboard Maestro.app, and I also take notes about the shortcuts under `System Preferences` > `Keyboard` > `Shortcuts` tab; I need to memorise the shortcuts from time to time in case of forgetting them. A tip is mapping `⇧r` to `⌃⌥⇧` is easy to memorise because the last key of the modifier combo is `⇧`; same for `⌘r` to `⌃⌥⌘`.

#### PCKeyboardHack

**Note:** Change Caps Lock Key to `No Action in `System Preferences` > `Keyboard` > `Keyboard` tab > `Modifier Keys...` button before mapping Caps Lock.

Key Name                    | New Key Value | New Key Name
---                         | ---           | ---
Caps Lock                   | 80            | F19
Command_R (in `Other Keys`) | 64            | F17
Option_R                    | 106           | F16
Shift_R                     | 79            | F18
{: rules="groups"}

#### Mouse keys

I also do some tricks on mouse thru [Keymo](http://manytricks.com/keymo/) ([MAS](https://itunes.apple.com/gb/app/keymo/id449863619?mt=12)). Also I set press `Fn` to moving a window like in Linux thru the free [BetterTouchTool](http://www.boastr.net/) `⌘,` > `Advanced` > `Action Settings tab` > `Window Moving & Resizing` > `Move windows` OR BetterSnapTool `⌘,` > `Extras` tab > `Move windows` (they are developed by the same developer and function the same; I have them both but got BetterTouchTool earlier).

![alt text](http://i.imgur.com/Fo1JPkC.png "Keymo")

#### More apps

I also have a keyboard/mouse toolkit including Chrome's extension **Vimium**; Firefox's extensions, **Pentadactyl** and **Vimperator**; MAS apps, **MenuMate**, **Yoink** or **Dropshelf**, and **RapidClick**, or maybe **Simplify for Spotify** (Alfred's Spotify workflow is not good for me); MAS apps that work with their iOS apps, **Command-C** and **1Keyboard**; and direct sale/beta/free apps, [**Shortcat**](http://shortcatapp.com/) and [**CheatSheet**](http://www.mediaatelier.com/CheatSheet/).

### Notes

A mindmap will be clearer, so I made one.

<a href="http://cl.ly/1T0x0Y2u2H27" class="btn btn-info">CloudApp</a>

You can do whatever you like but it's only for personal use.

**Update**: I forgot to mention TextExpander, though it's an snippet expander, it have fill-in fields which is quite cool! Also PopClip which performs macros on selected text. I set a shortcut to let the PopClip menu appear: use Automator to create a service which activated PopClip, save and then set a shortcut to the service under `System Preferences` > `Keyboard` > `Shortcuts` tab > `Services`.
