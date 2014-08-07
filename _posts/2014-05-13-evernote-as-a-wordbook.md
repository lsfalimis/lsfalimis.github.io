---
layout: post
title: "Evernote as a Wordbook"
description: "With Keyboard Maestro and PopClip"
category: Mac
tags: [Keyboard Maestro, Share]
comments: true
share: true
---

## Contents
{:.no_toc}

* 
{:toc}


### Function

Add a new word along with the sentence, a timestamp and the window title to your Evernote vocabulary note.

<!--more-->

I map `⇧_R` to `^⌥⇧` (see my blog for more info). Type `^⌥⇧1` to set the clipboard to the word and the meaning (from Google Translate). You will need to decide what to append to that word for this Evernote note, select that, and press `^⌥⇧2`. Done!

### Prerequisites

- You need to install Keyboard Maestro (KM) on your Mac and they are two KM macros.
- You need to install PopClip and the extension called [Instant Translate](https://pilotmoon.com/popclip/extensions/page/InstantTranslate).
- You need to install the macro called `Popclip Translate` which has already included in the bundle.

### How to download

Go to my KM repo and tap `Download ZIP`. After download, unzip it and double tap Wordbook.kmmacros to import.

<a href="https://github.com/lsfalimis/Qian-KM-Macros" class="btn">GitHub</a>

You are welcome to change the format to whatever you like, it's your custom wordbook!

### How to set the title of the vocabulary note

Open Keyboard Maestro and choose `__AS_[select sentence before keystroke!] append vocab to a EN note`, slide to the bottom, and within the edit are of the AppleScript, find and replace TARGETNOTE to your desired note title.

### Note
Given I'm ignorant of any programming knowledge, the defects of the solution is the vocabulary note's title has to be unique, which means there allows only one note with this title in your Evernote account.