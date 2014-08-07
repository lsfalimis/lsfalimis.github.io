---
layout: post
title: "PDF Note Taking Workflow"
description: "Highlighting Procedure: Chrome, Jstor, Hazel, Skim, Keyboard Maestro, AppleScript and Evernote"
category: Mac
tags: [AppleScript, Keyboard Maestro]
comments: true
share: true
---

## Contents
{:.no_toc}

* 
{:toc}

<!--more-->

### Download PDF

Download a random PDF file from Jstor in Chrome by tapping `Save Link As...` in the context menu of a downloadable hyperlink, and after download, from the bottom download bar, access the context menu and tap `Always Open Files of This Type` (If want to turn off, `⌘,` > `Show advanced settings` > Under `Downloads`, tap `Clear auto-opening settings`)

![alt text](http://i.imgur.com/paUWGo7.png "Insert")


Turn off Chrome built-in PDF viewer in `Chrome://plugins` (You will need to set Skim to be the default PDF reader: Go to Finder, select a file, `⌘I`, under `Open with:` tap the dropdown menu, choose Skim and tap `Change All...`; till now, Skim automatically open the PDF file **instead of** saving the file (move mouse, find save button, tap, wait, tap `Save`), close the Chrome PDF viewer tab, go to Finder, and double tap the file - it saves seven steps!)

⌘tap `View PDF` in Jstor (this will open in a tab and eliminate itself instead of annoying popup - it saves a step.)


### Sort the folder

[Hazel](http://www.noodlesoft.com/hazel.php) is a powerful tool to **automatically** sort files into folders and even run scripts on them. I really regretted for recently keeping changing the path of downloads folders for different projects (besides, it's huge pain to change this path as it involves many steps).

Keep Chrome downloads folder clean and let Hazel stay power. Set and let Hazel to trash .pdf and let Chrome stick to the same downloads folder all the time

![alt text](http://i.imgur.com/xXU08Ja.png "Insert")


### Index pages

Index the **print page number** instead of the PDF viewer's **index page number**. It has been a long-term problem for me when I was refering in my essay. Two of Stephen Margheim's great AppleScripts do the trick:

- Set the correct **print page number** [about](http://hackademic.postach.io/3-notes-that-should-be-on-every-pdf) [gist](https://gist.github.com/smargh/6068092)

- When export Skim notes, mark the notes with **print page number** [gist](https://gist.github.com/smargh/6480259) The code should be self-explaining, otherwise you need to check his blog [post](http://hackademic.postach.io/export-all-skim-notes-as-markdown-plain-text)

Another problem is the first AppleScript require you to manually rename the file firstly. (Refer to the previous part, you will know trash PDF files necessay to not to duplicate PDF files on your Mac.) However, even the most known Mac reference manager [Papers 3](http://www.papersapp.com/mac/) cannot guarantee correct naming each time, I believe we have to rely on ourselves.

Let KM set clipboard to "past clipboard 2 - past clipboard 1 - current clipboard" and set a shortcut

![alt text](http://i.imgur.com/4uu9hPt.png "Insert")

Then, in Skim, sequentially copy author name, year, and article title, and then press the shortcut.

Go to the project folder (if you open it in previous file saving, you don't need to folder switching) and ⌘V and save the file (yes, no duplication). I actually bind them togerther.

![alt text](http://i.imgur.com/8G3tnBS.png "Insert")

### Export notes to Evernote

Highlight in Skim and export notes to Evernote which refer to each page **instead of** the PDF file. I don't know which app rules the OS X PDF viewer, but the choice of many academic workflow bloggers of [Academic workflows on a Mac](http://blog.macademic.org/) and [The Hackademic](http://hackademic.postach.io/) is Skim. I have to say their insights about academic Mac workflows are so great that I'd like to use the tools they use.

The AppleScript is mentioned in the above [gist](https://gist.github.com/smargh/6480259) author's blog [post](http://hackademic.postach.io/export-all-skim-notes-as-markdown-plain-text)


**Save time, save energy, save attention.**