---
layout: post
title: "Print Acronyms in LaTeX"
description: ""
category: Mac
tags: [LaTeX]
comments: true
share: true
---

## Building

I remember printing a list of acronyms in LaTeX was troublesome a few years ago when I attempted to build the PDF file. This time `makeglossaries DOCNAME` will be enough. I has been relied on ST3's LaTeXTools plugin for a long time. However, I can't figure out how to edit LaTeX.sublime-build (according to [this](https://github.com/SublimeText/LaTeXTools/issues/20)), so I give up using LaTeXTools if I'm writing a LaTeX that need printing acronyms or glossaries. Note that when `pdflatex thesis.tex`, `.tex` can be neglected, so just `pdflatex thesis`.

{% highlight bash %}
➜  Draft  pdflatex thesis
zsh: command not found: pdflatex
➜  Draft  zshconfig
# add '/usr/texbin' to $PATH, so
# export PATH="/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin:$HOME/bin:/usr/texbin"
➜  Draft  pdflatex thesis
# should be working
➜  Draft  zshconfig
# add the following
# alias gls="cd PATH && pdflatex thesis > /dev/null 2>&1 && makeglossaries thesis > /dev/null 2>&1 && pdflatex thesis > /dev/null 2>&1 && open thesis.pdf"
{% endhighlight %}

## Writing

You can see the LaTeX file structure of my dissertation at [here](http://lsfalimis.github.io/dissertation-latex-structure/). Three places need to be noted. Firstly, when `\printglossary`, notice that it has the effect of `\newpage`, so don't add `\newpage` otherwise you will see an extra blank page. Secondly, if you want to produce a list of acronyms not glossaries, and use `\usepackage[acronym]{glossaries}` in the preamble and the commands such as `\newacronym`, `\gls`, `\acrshort` instead of other commands from `glossaries` package, then `\printglossaries` will print a list of acronyms for you, `\printglossary` will not. If you are sensible about the meaning of acronyms, and know 'acronyms' and 'abbreviations' are different, and you should title the list 'Abbreviations' not 'Acronyms', then you have to use `\printglossary`. So here I need to add options to let `\printglossary` print a list of acronyms for me, add 'type=\acronymtype' to make it work, and add `title=Abbreviations` to change title (see below).

### frontmatter.tex

{% highlight latex %}
\pagestyle{empty}
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

Next I will make a note about `\newacronym`, `\gls` and `\acrshort`

{% highlight latex %}
% create API term in the list of acronyms (LOA).
\newacronym{api}{API}{Application Programming Interface}
\begin{document}
% produce LOA
\printglossary[type=\acronymtype, title=Abbreviations]
% Assume this is page 1.
\newpage
% This is page 2.
\gls{api} will be shown as 'Application Programming Interface (API)'
(within the quotation marks)
which is linked to the API term in LOA
and will add a linked page number '2' after the API term.
\newpage
% This is page 3.
\acrshort will be shown as 'API'
(within the quotation marks)
which is linked to the API term in LOA
and will add a linked page number '3' after '2' and a comma.
{% endhighlight %}
