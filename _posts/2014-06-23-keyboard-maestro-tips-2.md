---
layout: post
title: "Keyboard Maestro Tips 2"
description: ""
category: Mac
tags: [Keyboard Maestro, Python, Shell]
comments: true
share: true
---

<figure>
	<img src="http://i.imgur.com/cpWwfBs.png" alt="">
	<figcaption><a href="http://localhost:4000/keyboard-maestro-tips-2/#taxonomy" title="KM Taxonomy">KM Taxonomy</a></figcaption>
</figure>

## Contents
{:.no_toc}

* 
{:toc}

## Example

I did a KM cleanup yesterday (not finish yet) and found I have stopped using many unnecessary Mac apps for some time. It's a good thing.

To expand the use of KM, I will have to dive into shell. Next I take an example about adding new words to Mac's spelling records.

<!--more-->

![alt text](http://i.imgur.com/4uRyKjR.png "Insert")

It's mainly three python scripts. Of course I can put them in just one script, but breaking them into three will help forming a KM module management. Besides, I don't like KM to generate extra files so I set it up in a way I can access the code within KM. So there are now shell commands.

### Get words

The first command is to get words using regex:

~~~ bash
python -c 'import sys;import re;print re.findall(r"\b[a-zA-Z]+\b",sys.argv[1])' "$KMVAR_rein"
~~~

`-c` allows the following python code running direct in shell. `$KMVAR_` is followed by a name of KM macro. I import `re` and want to get a list of words returned; I can't get a list but only one word if I use KM's regex action. And I set KM to save the printed result as a KM variable, `reout`.

### Append to a file

The second command is to append a list of strings to a file, creating new lines (with each item in the list in a new line):

~~~ bash
(echo "lst=$KMVAR_list";echo "f=open('$KMVAR_file','r+')";echo "f.seek(-1,2)";echo "f.write('''\n''') if f.read(1) != '''\n''' else ''";echo "f.close()";echo "f=open('$KMVAR_file','a')";echo "for e in lst: f.write('''%s\n''' % e)";echo "f.close") | python
~~~

You can notice that I put `$KMVAR_` in the python code rather use it as an argument or parameter passed to python command. I think I can do this because of I use `echo` here, anyway I'm not interested to figure it out. Next I need to make sure I append the first item of list in a blank line. However puting lines as a list for example `linelist`, and the last two lines of file is `second last line\n`. `linelist[-1]` will return `second last line\n` instead of `\n`. So I use `read` to tell if the last character is `\n`. Before that `seek` will move the cursor of `find` to a location I want. `2` in `seek(-1,2)` means from the bottom of the file. After getting know if the last line is empty, I loop the line to write in the file with line break. Because `\n` is recognised as a line break in `echo` so I have to wrap it with `'''` to make the string to write continued. I tried to write using `with open(PATHTOFILE, MODE) as VAR:` but it doesn't play well with `for` loop chunk...

### Sort alphabetically

The third command to alphabetise a list of lines in `$KMVAR_file` (here it's `/Users/henry/Library/Spelling/LocalDictionary`)

~~~ bash
(echo "with open('$KMVAR_file','r') as f: lst = sorted(f)"; echo "with open('$KMVAR_file','w') as f: f.writelines(lst)") | python
~~~

Python's sort command is very handy.

## Systematisation of good

Some more words about systematisation of KM macros to increase efficiency or good (善). 

1. For now, I think the best trigger is the pallette that consists of hot strings. You can have a very short glance to check the name of macro and rehearse the shortcuts; and thank God, I don't need to type like a robot that has a shortcuts cheatsheet coded inside it. If you accidently trigger a pallette, you don't need to worry, because macros haven't been triggered. 

2. I try to implement timestamp on KM; however, it can be easily forgotten. By the way, the comment title is searchable and the content is not.

3. I normally collapse the actions (see the screenshot below), so I will not happy if there is no title for `execute shell script` action and I don't want another `comment` action which will bloat the look. As a result, I save the shell script action as a macro and detail input/output KM variables in its macro.

	![alt text](http://i.imgur.com/L9MsKHy.png "Insert")

	![alt text](http://i.imgur.com/dXfzzgk.png "Insert")

4. I like Alfred's visualisation of workflow (but not good for setting app launch shortcuts, slow to set up and hard to modify). But through modularisation, KM workflows is responsive and won't look bad. Finally, about KM variable `pptalt`. It's a trick: save the clipboard conetent as a KM variable; after 2 seconds, set this variable empty.

	![alt text](http://i.imgur.com/ngppJRh.png "Insert")

## Taxonomy

This part is about the type of KM macros, KM taxonomy, Mac action taxonomy, or simply what's KM for. 

![alt text](http://i.imgur.com/cpWwfBs.png "Insert")

1. **Saves time.** I don't want to use my time to report bugs, send 'feature request' emails and wait.
	- For examples,
		- I think every 1Password user has it in iPhone as well as Mac, right? And mobile sync, if you are paranoia you must use Wi-Fi sync, is a prime daily use of 1Password. How come such important move is without a keyboard shortcut?!
		- Same for Evernote, another business-promoted, bloated, popularised app that lacks essential keyboard shortcuts, even menu items(! God...);
		- same for Tweetbot, another highly priced, bloated, popularised app that lacks menu items.
	- In a word, lack of shortcuts, lack of user documentation and lack of sincerity (诚意) given differnce in price and reality. So, the story is, ⌘9 to open Wi-Fi sync window is broken on my Mac then I have KM to fix it. Another thing is, ⌘W will quit 1Password. So next time I open 1Password I have to wait for it finish loading. Come on, developers, where is your consideration?
	- So in KM, I set when I press `⌘W`, please press `⌘H` instead. Sometimes, it seems to be an idea difference, so get it done with KM very quick instead of seeing the reply of developers. You also saving developers' time, as well :)
	- One more thing, previously I made a macro about 1Password to generate a new password, fill the website login URL in the new password item in 1Password, and fill the email or username in that website OR send to your other Apple devices (iPhone, iPad, or Mac) in another post. Another one is to log in the account in some buggy website (Sina Weibo) or desktop apps (iTunes) (see [here](http://i.imgur.com/sFGcECA.png)). 
	- I'd to give some more app examples.
		- Tweetbot doesn't have a back shortcut, so I make one, Escape key.
		- [Command-C](http://danilo.to/command-c) is a tool that will be shadowed by Yosemite, though I used just one key to copy and send.
		- [Little Snitch](http://www.obdev.at/products/littlesnitch/index.html) is a tool to cut the network communication between Mac app and the servers, and I use just one key to click on its endless popup windows that asks for permission. 

2. **Trigger right click menu.** I hate the design of right click menu. Get rid of feeling, use KM.

3. **Concatenates past clipboards** and customises the format if you like. KM is better than Alfred on this.

4. **Pastes browser information,** such as, the page title and URL of Chrome and Safari, and put them in a markdown syntax.

5. **Pastes processed texts.** The processing can be replacing text, capitalisation, title case, lowercase, uppercase, percent encode of URL, cutting kinds of path (file path and URL), regex filter, list split, list joining.

6. **Workflow expanded.** You can gather and pool fragmented unconscious moves on Mac whether it happens on desktop app or browser, you make a target for the computer, you streamline the pieces and ditch irrelevant waste of attention, and you are able to make a purpose for yourself; because right now you can have the computer listening to you, thought you are not mastering the machine; you can see the machine more clear, so yourself. You free the less meaningless in exchange for the space for the more meaningful. It's an evolution.



















