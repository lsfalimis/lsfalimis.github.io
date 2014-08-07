---
layout: post
title: "edX Linux Course Notes"
description: ""
category: Mac
tags: [Shell]
comments: true
share: true
---

## Contents
{:.no_toc}

* 
{:toc}

## About

The free course is [LFS101x: Introduction to Linux](https://courses.edx.org/courses/LinuxFoundationX/LFS101x/2T2014/info).

<!--more-->

Some CLI utilities are not shipped with OS X, so I use [Homebrew](http://brew.sh/) and [Cakebrew](https://www.cakebrew.com/) to install them:

{% highlight bash %}
ruby -e "$(curl -fsSL https://raw.github.com/Homebrew/homebrew/go/install)"
{% endhighlight %}

and then open Cakebrew to check information of things I want to install before installation.

## Commands

|---
|Something|What does it do?|
|-|-|-|
|Command||
`whereis`|Locate CLI utilities
`pwd`|Print the **p**resent **w**orking **d**irectory
`tree`|Produce a tree-like list of files
`pushd`|Remember a path to go back
`popd`|Go back to `pushd`ed path
`locate`|Seach filename with pattern option available
`find`|Similar to `locate`
`cat`|Print file
`tac`|Reverse `cat`
`less`|`cat` with pagination/pages
`head`|`cat` first 10 lines
`tail`|`cat` last 10 lines
`rmdir`|Delete an empty directory
`diff3 MY-FILE COMMON-FILE YOUR-FILE`|`diff` three files
`file`|Print filetype
`who`|List users
`whoami`|List user
`!!`|Called 'bang-bang'; redo
`alias`|List aliases
`chown`|read (r), write (w), execute (x) -> rwx \\
`chgrp`|user/owner (u), group (g), others (o) -> ugo, so uuugggooo or rwxrwxrwx \\
`chmod`|4 means read, 2 write, 1 execute, 7 rwx, 6 rw-, 5 r-x
`host`|I don't know
`nslookup`|I don't know
`dig`|I don't know
`curl`|`wget` files and the webpage
`sftp`|I don't know
`scp`|I don't know
`sed`|Stream editor
`awk`|Works with fields (columns) and records (rows)
`sort`|Sort lines in file
`uniq`|Remove duplicate lines and need them consecutive, so `uniq` after `sort`
`join`|Remove duplications then `paste`
`split`|Break up a file into files with each having 1000 lines
`tr`|Replace
`tee`|Save piped output to file
`wc`|Count; or `wc -lcw` where means lines, characters and words
`cut`|Extract columns, e.g. `cut -d" " -f3`
`strings`|Extract printable (?) characters then for `grep`
`env`|Print environment variables
`set`|Print environment variables
`printenv`|Print environment variables
|---
|Command syntax||
`cd`|`cd ~`
`cd -`|Go back
`ls -a`|List all including hidden files
`ls -l`|List files in columns
`ls -i`|List files with unique inode numbers
`locate` pattern|E.g., `[adf]`,`[!adf]`,`[a-s]`,`[!a-s]`
`cat > FILE << EOF ↩ ... ↩ EOF`|Multiple lines; EOF can be replaced by any string
`cat > FILE ↩ ... ↩ ^D`|`cat > FILE << EOF ↩ ... ↩ EOF`
`find -name sth`|Search by name
`find -iname sth`|Ignore case
`find -type TYPE`|`d` directory, `l` symbolic link
`find -exec rm {} ’;’`|Or `find -exec rm {} \;`; I don't know
`find -ok rm {} ’;’`|Interactive `-exec`
`find -ctime N`|Last `N`th day of inode meta-data change, in most cases, file creation; if `N` is 0, means today
`find -atime +N`|Last `N`th day of file that is **a**ccessed or read; `+` greater
`find -mtime -N`|Last `N`th day of file that is **m**odified or written; `-` less
`find -size +10M`|In size that is over 10M
`touch -t 03201600 FILE`|With timestamp of March 20 1600
`touch FILE1 FILE2`|Can be followed by multiple files
`rm -rf`|Very dangerous; do not use
`rm –i`|Delete a file interactively
`rm –f`|Delete a file directly
`diff -c`|Content of 3 lines
`diff -r`|Also subdirectories
`diff -i`|Ignore case
`diff -w`|Ignore spaces and tabs (**w**hite space)
`diff -Nur originalfile newfile > patchfile`|I don't know `-Nur`
`patch originalfile patchfile`|Apply a patch to a file 
`patch -p1 < patchfile`|Apply a patch to the directory
`tar xvf mydir.tar`|Extract
`tar zcvf mydir.tar.gz`|gzip
`tar jcvf mydir.tar.bz2`|bz2
`tar Jcvf mydir.tar.xz`|xz
`tar xvf mydir.tar.gz`|gzip
`cat file1 file2`|**C**onc**at**enate files
`echo -e`|I don't know
`sed -e`|Execute multiple rules in a line, e.g. `sed -e 's/01/JAN/' -e 's/02/FEB/'`
`sed -f SCRIPT FILE`|Execute sed script on FILE
`sed s/pattern/replace_string/g file > file2`|`g` means the rule is effective on all occurrences
`awk '{ print $0 }' /etc/passwd`|Print entire file
`awk -F: '{ print $1 }'` /etc/passwd|Print the first column, I don't know `-F:`
`awk -F: '{ print $1 $6 }'`|Print the first and sixth column, separated by space
`cat file1 file2 | sort`|`cat` then `sort`
`sort -r`|reverse `sort`
`sort -u`|`uniq`
`uniq -c`|Count duplicate lines; I don't know
`paste -d`|Set delimiter, e.g., `paste -d ':' file1 file2`, `paste -d, file1 file2`
`paste -s`|horizontal `paste`; I don't know
`grep [pattern] file`|Print matched lines
`grep -v [pattern] file`|Print unmatched lines
`grep -C 3`|Print with the context of 3 lines
`cat city | tr a-z A-Z`|Nothing needs to say
`tr '{}' '()' < inputfile > outputfile`|Nothing needs to say
`echo "This is for testing" | tr [:space:] '\t'`|Replace spaces with tabs
`echo "This is for  testing" | tr -s [:space:]`|`-s` Squeeze spaces
`tr -d`|Delete
`echo "my username is 432234" | tr -cd [:digit:]`|To complement? I don't know
`tr -cd [:print:] < file.txt`|Remove non-printable characters? I don't know
`tr -s '\n' ' ' < file`|Join lines in a single line
`chmod +x FILE`|Make FILE executable for all users, then can `./file.sh`
`read VAR`|Save input as VAR
`TEMP=$(mktemp /tmp/tempfile.XXXXXXXX)`|`touch` a temporary file with a random filename
`TEMPDIR=$(mktemp -d /tmp/tempdir.XXXXXXXX)`|`mkdir` a temporary folder with a random filename
|---
|Something|In use|
`..`|`cd ../../usr/bin`
`2>`|Redirect stderr
`2>&1`|I don't know
`>&`|I don't know
`|`|Pipe symbol
|Shortcuts|Actions|
`^R`|Search used commands
`^L`|`clear`
`\n`|New line
`\t`|Tab
For compressed files|`zcat`, `zless`, `zdiff`, `zgrep`, `zmore` (?), `bzcat`, `bzless`, `xzcat`, `xzless`
`cmd1;cmd2`|Ignore failure
`cmd1 && cmd2`|Don't ignore failure
`cmd1 || cmd2`|Run cmd until success
`$(CMD)`|Take output of CMD as part of another CMD, e.g., the part of path that is to `cd`; or you can enclos by back ticks
`ls file > /dev/null 2>&1` then check `$?`|Don't print (like `qui` in Stata) and just check if succeed; `/dev/null` is called bit bucket or black hole.
`${#stringvar}`|Length of stringvar
`${string:0:1}`|`0` is the offset (the beginning position) and `1` is the number of characters to be extracted.
`${string#*.}`|Extract all characters; what's the difference with `string`?
`$RANDOM`|An environment variable; Linux kernel’s built-in function; or can use OpenSSL library function (what's the cmd?) that uses the FIPS140 algorithm
|
{: rules="groups"}

## Descriptors

There are three file streams (or descriptors) in shell: standard in(put) (stdin), standard out(put) (stdout) and standard error (or stderr). Open files are represented by descriptors. stdin is 0, stdout 1, stderr 2, open file 1 descriptor 3... We can realise I/O Redirection using `>` (overwrite to outside command), `>>` (append to outside command), `<` (take in as part of command), `<<` (take in the command by appending; I'm not so sure).

## Paths

|---
|Path|Files|
|-|-|-|
`/bin`|Essential executable binaries
`/usr/bin`|Less essential
`/sbin`|Essential system administration tools
`/usr/sbin`|Less essential system administration tools
{: rules="groups"}

Initiating order:

1. `~/.bash_profile`
2. `~/.bash_login`
3. `~/.profile`

## IP

A--E class of IP: IP = Net ID + Host ID for A--C class; D class is used for multicast (broadcast information to multiple computers simultaneously); and E class is reserved for the future. IP is divided into four octets: octet1 is Net ID for A class (1.0.0.0--127.255.255.255), 1--2 B (128.0.0.0--191.255.255.255), and 1--3 C (192.0.0.0--223.255.255.255). IPs are requested from Internet Service Provider (ISP). IP can be static or dynamical which then will use Dynamic Host Configuration Protocol (DHCP) to assign IPs.

## Variables

Functions are also called subroutines and `$1` means the first argument. Beside, `$0` means script filename, `$*` all arguments, `$#` number of arguments.

## Constructs

### Conditionals

{% highlight bash %}
if condition; then statement; fi
{% endhighlight %}

{% highlight bash %}
if condition
then
	statement
else
	statement
fi
{% endhighlight %}

{% highlight bash %}
if condition
then
	statement
elif condition
then
	statement
else
	statement
fi
{% endhighlight %}

{% highlight bash %}
case "$VAR" in
	"a"|"A") echo "Vowel" ;;
	"e"|"E") echo "Vowel" ;;
	"i"|"I") echo "Vowel" ;;
	"o"|"O") echo "Vowel" ;;
	"u"|"U") echo "Vowel" ;;
	*) echo "Consonant" ;;
esac
{% endhighlight %}

### Looping constructs

{% highlight bash %}
$sum=0
for i in 1 2 3
do
	sum=$(($sum+$i))
done
{% endhighlight %}

{% highlight bash %}
for filename in $(ls)
	ext=${filename##*\.}
	case "$ext" in 
		c) echo "filename : C source file"
		...
		*) ...
	esac
done
{% endhighlight %}

{% highlight bash %}
while trueCondition
do
	statement
done
{% endhighlight %}

{% highlight bash %}
until falseCondition
do
	statement
done
{% endhighlight %}

### Tests

#### File tests

- See see `man 1 test`
- `-e file` checks if exists.
- `-d file` checks if is a directory.
- `-f file` checks if is a regular file (i.e., not a symbolic link, device node, directory, etc.)
- `-s file` checks if is of non-zero size.
- `-g file` checks if has sgid (?) set.
- `-u file` checks if has suid (?) set.
- `-r file` checks if is readable.
- `-w file` checks if is writable.
- `-x file` checks if is executable.

#### Numerical tests

- `exp1 -op exp2`
- `-eq` means equal to
- `-ne` means not equal to
- `-gt` means greater than
- `-lt` means less than
- `-ge` means greater than or equal to
- `-le` means less than or equal to

#### Arithmetic expressions

Note the spaces: `expr 8 + 8`, `echo $(expr 8 + 8)`, `echo $((x+1))`, `var=$((...))`

#### String tests

`[ string1 > string2 ]` compare the sorting order; `[ string1 == string2 ]` you know, compare; `!` not.

## Debugging

`gdb` and `valgrind` and I don't know.

`bash –x ./script.sh` turns debug mode on. Or within script.sh, use `set -x` to turn on, `set +x` off.

## Processes

There are interactive processes, batch processes, daemons, threads, and kernel threads; child process, parent process, zombie process. Process are tracked by process ID (PID) numbers, also Parent Process ID (PPID), Thread ID (TID), Real User ID (RUID), Effective User ID (EUID) of whom determines the access rights for the users, Real Group ID (RGID) about the group of users, and Effective Group ID (EGID). The lower the nice value ([-20, 19]), the higher the priority, the more time granted to use CPU, the less time to wait, aka, the less elapsed time. Besides, real-time priority is available.

## Terms

tar means 'tape archive'. tar archive file is called tarball.

`gcc` is C and C++ compiler.

