---
layout: post
title: "AppleScript-Python Passing Filename"
description: "Use AppleScript to Get Filename Without Extension, Set Custom Delimiters and Pass Mutiple Parameters to a Python Script"
category: Mac
tags: [AppleScript, Share]
comments: true
share: true
---

## Contents
{:.no_toc}

* 
{:toc}

<a href="https://gist.github.com/lsfalimis/a52a6de6c7471dfb9e66" class="btn btn-success">Gist</a>

<!--more-->

### It's Simple

It's a note just in case I forget it.

Firstly, I treat you or myself as a person who know nothing about AppleScript (AS thereafter) or coding.

### Declare Codes to an App

To run an action (actually my scripting journey started from iOS with Drafts which symbolically called a trigger, some codes, a launcher as a action to my understanding, so take it easy), I need to write

{% highlight applescript %}
tell application "APPNAME"
	SOMECODES
end tell
{% endhighlight %}

### How to Set a File Input?

In Hazel, running an AS on the target file requires a simple placeholder `theFile`. Here I'm going to write in AppleScript Editor (which is a stock app of OS X), and check the output within AppleScript Editor. So I need to know how to set a file input. We know Hazel before AS, so I let the naming rules inherit from the people's app but not from deeply hid language or something.

Note that AS uses HSF path. For me, simply buy a copy of Path Finder and copy HSF path in that app. XtraFinder is free, but for me, Path Finder is expensive and complex and after trying for some time I believe it's the best alternative to Finder.

{% highlight applescript %}
set theFile to "Macintosh SSD:Users:henry:Desktop:1.py”
{% endhighlight %}

### How to Save Outputs in an External File?

This's useful when the outputs include special characters, such as `\"`, and maybe only in the external file, you can have confidence to say that's the correct outputs you want.

{% highlight applescript %}
do shell script "echo " & VARIABLE & " > ~/Desktop/test.txt"
{% endhighlight %}

### Group Codes Using `()`

I can group one action with a pair of parentheses. This could be vague, just do some tests to see the grouping's effects yourself.

### Get Filename

`alias` needs to be used.

{% highlight applescript %}
set theName to name of (theFile as alias)
{% endhighlight %}

### Get Rid of Extension

Note that name and extension are devided by ".", and for example the file is `1.py`, by `set AppleScript's text item delimiters to "."`, from left to right, the first **text item** is `1`, the second **text item** is `py`, corresponding, in AS, the value of `text item 1` is `1` and the value of `text item 2` is `py`. From right to left, the first text item is marked as `-1`. So the value of `text item -1` is `py` and the value of `text item -2` is `1`.

{% highlight applescript %}
set theName to name of (theFile as alias)
set AppleScript's text item delimiters to "."
if number of text items of theName > 1 then
	set theName to text items 1 thru -2 of theName
end if
{% endhighlight %}

Later I will chain the AS to a Python script and I don't want another delimiter, so I continue to use "." and negative text item becomes seemingly more meaningful, because, the number of parameters to pass to the Python script is uncertain.

### How to Check Data Type

In coding, data type is always important. Beginner should not mistake them. Because I cannot pass a data, whose type is a list, to Python script and maintain the data as a list type data. So I do it in a hard way. Ok, before that, to check the data type is simple. Type `class DATA` in a single line, and tap Run button, the below output row will show the returned result.

### Pass A List to Python

{% highlight applescript %}
set theItems to ""
repeat with i from 1 to count of theName
	set theItems to theItems & "\"" & ((item i of theName) as text) & "\"" & ","
end repeat
set theItems to text 1 thru -2 of theItems
{% endhighlight %}

Here `"\""` means character `"`, and for example `theName` is `a.b`, then the final value of `theItems` is `"a","b"`. I already have curly brackets ready in the Python script, so it will finally become `{"a","b"}`, which is a list type data in Python.

#### Pass a Workable File Path to a Python Script in AS

{% highlight applescript %}
set thePath to POSIX path of theFile
do shell script "python /PATH/TO/THE/PYTHON/SCRIPT" & theItems & " " & quoted form of thePath
{% endhighlight %}

At last, don't forget put `end tell` at the end of the AS.

If you have a workable and meaningful Python Script to test with the AS, that's good, otherwise the above will be less meaningful to look at.

The final AS is

{% highlight applescript %}
tell application "Finder"
	
	set theName to name of (theFile as alias)
	set AppleScript's text item delimiters to "."
	if number of text items of theName > 1 then
		set theName to text items 1 thru -2 of theName
	end if
	
	set theItems to ""
	repeat with i from 1 to count of theName
		set theItems to theItems & "\"" & ((item i of theName) as text) & "\"" & ","
	end repeat
	set theItems to text 1 thru -2 of theItems
	
	set thePath to POSIX path of theFile
	
	do shell script "python /PATH/TO/THE/PYTHON/SCRIPT" & theItems & " " & quoted form of thePath
	
end tell
{% endhighlight %}

