---
layout: post
title: "Dissertation LaTeX Structure"
description: ""
category: Mac
tags: [LaTeX]
comments: true
share: true
modified: 2014-08-16
---

<!--more-->

This is my LaTeX working directory. Because `Draft` is so messy, it always take a long time for me to find `tex` file and `pdf` file so I spilt a `tex` file into many. Because I'm a bad student as welll as a bad writer, I choose not to divide the chapters at the beginning. I will divide them when I'm writing the dissertation.

{% highlight bash %}
├── Chapters
│   ├── concl.tex
│   ├── draft.tex
│   └── intro.tex
├── Draft
│   ├── after.tex
│   ├── before.tex
│   ├── thesis.acn
│   ├── thesis.acr
│   ├── thesis.alg
│   ├── thesis.aux
│   ├── thesis.bbl
│   ├── thesis.bcf
│   ├── thesis.blg
│   ├── thesis.fdb_latexmk
│   ├── thesis.glg
│   ├── thesis.glo
│   ├── thesis.gls
│   ├── thesis.ist
│   ├── thesis.lof
│   ├── thesis.log
│   ├── thesis.lot
│   ├── thesis.out
│   ├── thesis.pdf
│   ├── thesis.run.xml
│   ├── thesis.tex
│   └── thesis.toc
├── Inputs
│   ├── acronyms.tex
│   ├── backmatter.tex
│   ├── expanders.tex
│   ├── frontmatter.tex
│   ├── info.tex
│   ├── mainmatter.tex
│   ├── settings.tex
│   └── titlepage.tex
└── bib.bib
{% endhighlight %}

## thesis.tex

{% highlight latex %}
\input{before}

I write here.

\input{after}
{% endhighlight %}

## before.tex

{% highlight latex %}
\documentclass[a4paper,12pt]{report}

\input{../Inputs/settings}

\input{../Inputs/expanders}

\input{../Inputs/acronyms}

\begin{document}

\input{../Inputs/info}

\input{../Inputs/frontmatter}

\chapter{Introduction}

\pagenumbering{arabic}

\chapter{Draft}
{% endhighlight %}

## after.tex
{% highlight latex %}
\chapter{Conclusion}

\input{../Inputs/backmatter}

\end{document}
{% endhighlight %}

## info.tex
{% highlight latex %}
\renewcommand{\title}{something}

\newcommand{\subtitle}{something}

\renewcommand{\author}{somebody}

\newcommand{\supervisor}{somebody}

\newcommand{\studentID}{something}

\newcommand{\dept}{something}

\newcommand{\university}{something}

\newcommand{\submissiontext}{\textbf{Declaration:} This dissertation is submitted in part fulfilment of the requirements for \degree. something}

\renewcommand{\degree}{something}

\newcommand{\degreedate}{something} % It's a shame I don't know how to get the word of the month.
{% endhighlight %}

## frontmatter.tex

{% highlight latex %}
%\pagestyle{empty}
\input{../Inputs/titlepage}

\newpage
\pagenumbering{roman}
\addcontentsline{toc}{chapter}{Acknowledgements}

\newpage
\addcontentsline{toc}{chapter}{Abstract}

\newpage
\tableofcontents

\newpage
\addcontentsline{toc}{chapter}{List of Figures}
\listoffigures

\newpage
\addcontentsline{toc}{chapter}{List of Tables}
\listoftables

\addcontentsline{toc}{chapter}{Abbreviations}
\printglossary[type=\acronymtype, title=Abbreviations]
{% endhighlight %}

Note that in `report` document class, `\pagestyle{empty}` will result in only the first page of every chapter to display page number. To solve the problem, use `titlepage` environment in the title page, that is, use `\begin{titlepage}` and `\end{titlepage}`.

## mainmatter.tex

{% highlight latex %}
\newpage
\pagenumbering{arabic}

\input{../Chapters/something1}

\input{../Chapters/something2}

\input{../Chapters/somethingN}
{% endhighlight %}

## backmatter.tex
{% highlight latex %}
\newpage
\addcontentsline{toc}{chapter}{References}
\chapter*{References}
\printbibliography
{% endhighlight %}