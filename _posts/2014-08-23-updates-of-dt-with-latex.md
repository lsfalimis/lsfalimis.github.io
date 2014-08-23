---
layout: post
title: "Updates of Dissertation With LaTeX"
description: ""
category: Mac
tags: [LaTeX]
comments: true
share: true
---

The deadline is coming closer but I'm so tired struggling with semiotic concepts...

## Contents
{:.no_toc}

* 
{:toc}

<!--more-->

## Use 'book' for 'twoside' 

I was convinced to use the `report` `documentclass`, but I just knew that my dissertation shall be bound, so I have to use `book` `documentclass`. But during writing, I still reply on using `report` for preview. Note that `openright` will allow every chapter to start on right-sided page. It's default for `book`, not default for `report` and here it's just a reminder.

{% highlight latex %}
\documentclass[a4paper,12pt,openright]{book}
{% endhighlight %}

## Normal Abbreviations

{% highlight latex %}
\usepackage[acronym,nonumberlist,nopostdot]{glossaries}
{% endhighlight %}

Page numbers and the period should be omitted by default...

## Divide References into parts

I was required to separate 'non-academic sources' (magazine, blog articles, etc.) from 'academic sources'. Besides, I want the title `Bibliography` changed to `References`. For me, bibliography is what I think may be useful for readers for further reading so put here, and references are what I have in-text citations (if I use Harvard style; or strict 'footnotes' if I use Oxford style) in my main texts. Thus, readers may expect `References` with in-text citations (or strict 'footnotes') with page number quoted. As for `Bibliography`, readers do not even expect the corresponding in-text citation (or strict 'footnote') exist! The final point is that Oxford style always get you MUCH closer to the word count. Although I'm not a good student who love to read more and write more, I don't like Oxford style.

{% highlight latex %}
\defbibheading{aca}{{"{%"}}
  \chapter{References}
  \subsection*{Academic Source}}
\defbibheading{nonaca}{\subsection*{Non-academic Source}}
\defbibheading{data}{\subsection*{Data Source}}
{% endhighlight %}

Then before `\end{document}`, add this,

{% highlight latex %}
%\nocite{*}
\printbibliography[heading=aca,notkeyword=not,notkeyword=nonaca,notkeyword=data]
\printbibliography[heading=nonaca,notkeyword=not,keyword=nonaca,notkeyword=data]
\printbibliography[heading=data,notkeyword=not,keyword=data]
{% endhighlight %}

To explain, I have a lot reading materials in BibDesk and some of them are not that meaningful for my dissertation. So I simply mark them with keyword `not` and in LaTeX file, add `notkeyword=not` option in the above code. You may use `type=book`, `nottype=article`, etc., but this is not appropriate for me to do so in my dissertation (I have asked).

Note: `\nocite{*}` include all items from `.bib` file in the list produced by `\printbibliography`, which helps you to do a test. Besides, I will explain in the next part that use `\chapter` in stead of `\chapter*` is to let `fancyhdr` to correctly display chapter title in the header. Because `fancyhdr` dependes on `secnumdepth` to decide chapter title ([ref](http://tex.stackexchange.com/questions/160758/fancyhdr-messes-up-with-backmatter)) and `\chapter*` seemingly does not produce `secnumdepth`, then I use `\chapter` that surely produce `secnumdepth`.

## Use 'fancyhdr' in 'book' 

### Header I like

{% highlight latex %}
\fancyhf{}
\renewcommand{\headrulewidth}{0pt}
\fancyhead[LE,RO]{\thepage}
\fancyhead[RE,LO]{\nouppercase{\leftmark}}
{% endhighlight %}

First, `\fancyhf{}` removes all headers. Then, the second line removes the rule. Next, L is top-left, R is top-right, O is the page with odd page number, E is the page with even page number, `\thepage` is the page number to display, `\nouppercase` will produce capitalised '"chapter" + chapter number + chapter title' or section if section is available and `\leftmark` is to let chapter is always shown.

### With normal blank pages

`openright` may produce a left-sided blank page to make right-sided the first page of a chapter. This blank page shouldn't have a header. Add this (from `fancyhdr` doc) to the preamble,

{% highlight latex %}
\makeatletter
\def\cleardoublepage{\clearpage\if@twoside \ifodd\c@page\else
  \hbox{}
  \thispagestyle{empty}
\newpage
  \if@twocolumn\hbox{}\newpage\fi\fi\fi}
\makeatother
{% endhighlight %}

will automatically remove the header.

### Display correct chapter title

Before I did the following steps, the headers of the references pages were `Abbreviations`, which was quite annoying. I have mentioned a little in 'Divide References into parts', and I don't want display chapter number in the table of contents, what should I do? Use `book` `documentclass`, add `\backmatter` before the command blocks of `\printglossary` and `\printbibliography`, and add the following in the preamble,

{% highlight latex %}
\makeatletter
\renewcommand\chaptermark[1]{
    \markboth{\MakeUppercase{{"{%"}}
      \ifnum\c@secnumdepth>\m@ne\if@mainmatter
         \@chapapp\ \thechapter. \ \fi\fi #1}}{}%
}
\makeatother
{% endhighlight %}














