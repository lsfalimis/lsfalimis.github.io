---
layout: post
title: "LaTeX Notes"
description: "Write like a Pro"
category: Mac
tags: [LaTeX]
comments: true
share: true
---

<script type="text/javascript"
    src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>

<figure>
    <img src="http://i.imgur.com/qyFP7we.png" alt="">
</figure>

## Contents
{:.no_toc}

* 
{:toc}

<!--more-->

## Basic Structure

{% highlight latex %}
\documentclass{...}

\begin{document}
...
\end{document}
{% endhighlight %}

Use `\documentclass[a4paper]{article}` to start. On document classes (article, book, beamer, etc.) and options, see [Wikibooks](http://en.wikibooks.org/wiki/LaTeX/Document_Structure#Document_classes).

## Preamble

### \usepackage

The preamble is the area between `\documentclass{...}` and `\begin{document}` where we can use the `\usepackage` command at the beginning:

{% highlight latex %}
\usepackage[T1]{fontenc}
\usepackage{ae,aecompl,microtype,amsmath,amsthm,amssymb,mathtools,empheq,bm,siunitx,accents,floatrow,subfig,caption,float,wrapfig,booktabs,array,multirow,threeparttable,tablefootnote,tikz,pgfplots,hyperref,listings,graphicx}
\usepackage[integrals]{wasysym}
\usepackage[style=verbose,backend=bibtex]{biblatex}
% \renewcommand{\familydefault}{\sfdefault}
{% endhighlight %}

I copy or paraphrase some sentences from [CTAN](http://www.ctan.org/) (Comprehensive TeX Archive Network). You can search package information by adding <http://www.ctan.org/pkg/%s> as a Chrome's search engine. Note some package can't be found using this URL, for example, aecompl. Then you will need to google it.

#### Font Rendering

> - fontenc [T1] - 'selecte font encoding', activate EC fonts / T1 font en­cod­ing
> - ae - 'al­most Euro­pean', vir­tual fonts which em­u­lates T1 coded fonts us­ing the stan­dard CM fonts
> 	- pro­duce PDFs us­ing Type 1 ver­sions of the CM fonts in­stead of bitmapped EC fonts
> - aecompl - add the characters missing in the ae fonts as bitmaps

On T1, ae, aecompl, see ["High quality PDF output from LaTeX and TeX"](http://dsanta.users.ch/resources/type1.html)

> - microtype - 'mi­cro-ty­po­graphic ex­ten­sions', subliminal refinements towards typographical perfection: char­ac­ter pro­tru­sion, font ex­pan­sion, etc.

On microtype, see ["Tips on Writing a Thesis in LaTeX: Microtype"](http://www.khirevich.com/latex/microtype/)

You can also change fonts. `\renewcommand{\familydefault}{\sfdefault}` changes the default font, Computer Modern Serif, to Computer Modern Sans Serif. More on changing font, see [this](http://www.forkosh.com/pstex/latexcommands.htm).

#### Environments or Objects

We can sort objects in LaTeX into different *environments*. According to [Wikia](http://latex.wikia.com/wiki/List_of_LaTeX_environments), there are

- Float: figure, table
- List: description, enumerate, itemize
- Math: math, displaymath, array, eqnarray, equation, theorem
- Matrix: cases, align
- Paragraph: center, flushleft, flushright, minipage, quotation, quote, verbatim, verse
- Picture
- Table: tabular
- thebibliography
- titlepage

The order of declarations matters, so when errors come out, you need to debug yourself by googling or other methods.

##### Maths

> - amsmath - 'American Mathematical Society (AMS) mathematical facilities'
> - amsthm - typeset AMS style theorems
> - amssymb - provide an extended symbol collection [(PDF)](http://milde.users.sourceforge.net/LUCR/Math/mathpackages/amssymb-symbols.pdf)

On AMS packages, see [StackExchange](http://tex.stackexchange.com/questions/32100/) and AMS's [Short Math Guide for LaTeX (PDF)](ftp://ftp.ams.org/pub/tex/doc/amsmath/short-math-guide.pdf)

> - mathtools - math­e­mat­i­cal type­set­ting tools to use with amsmath
> - empheq - 'EMPHasizing EQuations', to put a set of equa­tions in­side a box thus en­hanc­ing ams­math's \boxed
> - bm - access bold symbols in maths mode
> - siunitx - 'Le Système international d'unités (SI) or the international system of units units package'
> - accents - multiple mathematical accents

##### Floats

> - floatrow - cus­tomize layouts of floats; of­fers mech­a­nisms
> 	- to put floats side by side
> 	- to put the cap­tion be­side its float
> - subfig - figures broken into 'subfigures'
> 	- It is con­ve­nient to use this pack­age when your sub­fig­ures are to be sep­a­rately cap­tioned or ref­er­enced.
> - caption - customise captions in floats
> - float - introduce the boxed float, the ruled float and the plain­top float; provide the H option for floats
> - wrapfig - allow fig­ures or ta­bles to have text wrapped around them

##### Tables

> - booktabs - 'publication quality tables'; provide be­hind-the-scenes op­ti­mi­sa­tion
> - array - extend the array and tabular environments
> - multirow - create tabular cells spanning multiple rows
> - threeparttable - tables with captions and notes; no need for foot­notes
> - tablefootnote - permit footnotes in tables; provide \table­foot­note

##### Drawing Graphics

> - tikz - a recursive acronym for 'TikZ ist _kein_ Zeichenprogramm' (German for 'TikZ is _not_ a drawing program'); create PostScript and PDF graphics
> - pgfplots - draw plots in two and three dimensions; based on PGF/TikZ

#### Miscellaneous

> - hyperref - 'support for hypertext and cross-ref­er­enc­ing'
> - listings - typeset code listings
> - graphicx - enhanced support for graphics; improve \in­clude­graph­ics
> - wasysym [integrals] - WASY2 (Waldi Sym­bol) fonts by Roland Waldi
> - biblatex [style=verbose,backend=bibtex] - bibliographies using BibTeX for sorting only

### Other Package Specifications

{% highlight latex %}
\addbibresource{references.bib}
\sisetup{group-separator = {,}}
\usetikzlibrary{arrows,shapes,positioning}
\pgfplotsset{compat=1.8}
\pgfplotsset{soldot/.style={color=black,only marks,mark=*}}
\pgfplotsset{holdot/.style={color=black,fill=white,only marks,mark=*}}
\delimitershortfall-1sp
\floatsetup[table]{footposition=bottom}
{% endhighlight %}

- `\sisetup{group-separator = {,}}` adds thousand separators.
- `\delimitershortfall-1sp` adjusts the size of nested parentheses.

### New Command Declarations

{% highlight latex %}
\newcommand\abs[1]{\left|#1\right|}
\newcommand*\widefbox[1]{\fbox{\hspace{2em}#1\hspace{2em}}}
\newcolumntype{C}[1]{>{\centering\arraybackslash}p{#1}}
\DeclarePairedDelimiter\ceil{\lceil}{\rceil}
\DeclarePairedDelimiter\floor{\lfloor}{\rfloor}
\DeclareMathOperator{\sech}{sech}
\DeclareMathOperator{\csch}{csch}
\DeclareMathOperator{\arcsec}{arcsec}
\DeclareMathOperator{\arccot}{arcCot}
\DeclareMathOperator{\arccsc}{arcCsc}
\DeclareMathOperator{\arccosh}{arcCosh}
\DeclareMathOperator{\arcsinh}{arcsinh}
\DeclareMathOperator{\arctanh}{arctanh}
\DeclareMathOperator{\arcsech}{arcsech}
\DeclareMathOperator{\arccsch}{arcCsch}
\DeclareMathOperator{\arccoth}{arcCoth}
\DeclareMathOperator*{\plim}{\mathnormal{p}\mkern2mu-lim}
\definecolor{color1}{RGB}{249,215,177}
\newcommand\gauss[2]{1/(#2*sqrt(2*pi))*exp(-((x-#1)^2)/(2*#2^2))}
\newtheorem*{thm}{Theorem}
\newlength{\dhatheight}
{% endhighlight %}

You can let new commands having no parameter,

{% highlight latex %}
\newcommand{\A}{\alpha}
\newcommand{\sg}{\sigma}
\newcommand{\is}{_i^2}
\newcommand{\Yi}{Y_i}
\renewcommand{\Xi}{X_i}
\newcommand{\lyi}{y_i}
\newcommand{\ey}{\hat{Y}}
\newcommand{\eu}{\hat{u}}
\newcommand{\esg}{\hat{\sg}}
\newcommand{\mr}{\mathrm}
\renewcommand{\S}{\sum}
\renewcommand{\bold}{\textbf}
\newcommand{\TA}{\T{Assets}}
\newcommand{\TP}{\T{Personnel}}
\newcommand{\TE}{\T{Expenditure}}
{% endhighlight %}

or having parameters.

{% highlight latex %}
\newcommand{\B}[1]{\beta_{#1}}
\newcommand{\eb}[1]{\hat{\beta}_{#1}}
\newcommand{\pt}[1]{{\left(#1\right)}}
\newcommand{\bk}[1]{{\left[#1\right]}}
\newcommand{\T}[1]{\text{#1}}
\newcommand{\Xni}[1]{X_{#1i}}
\renewcommand{\ni}[1]{x_{#1i}}
{% endhighlight %}

Sometimes a new command declaration can be complex:

{% highlight latex %}
\newcommand{\doublehat}[1]{ %
    \settoheight{\dhatheight}{\ensuremath{\hat{#1}}}%
    \addtolength{\dhatheight}{-0.35ex}%
    \hat{\vphantom{\rule{1pt}{\dhatheight}}%
    \smash{\hat{#1}}}}
{% endhighlight %}

Note that if the desired command name has already existed, you need to use `\renewcommand`.

### Title Page

There are many at [LaTeX Templates](http://www.latextemplates.com/cat/title-pages)

Here is an example:

{% highlight latex %}
\newcommand*{\titleAT}{\begingroup % Create the command for including the title page in the document
\newlength{\drop} % Command for generating a specific amount of whitespace
\drop=0.1\textheight % Define the command as 10% of the total text height
    
\centering
\rule{\textwidth}{1pt}\par % Thick horizontal line
\vspace{2pt}\vspace{-\baselineskip} % Whitespace between lines
\rule{\textwidth}{0.4pt}\par % Thin horizontal line
    
\vspace{\drop} % Whitespace between the top lines and title1
{\Huge Anything}\\[0.5\baselineskip] % Title line 1
{\Large of}\\[0.75\baselineskip] % Title line 2
{\Huge Anything}\\[0.75\baselineskip]
{\Huge and Anything} % Title line 3
    
\vspace{0.25\drop} % Whitespace between the title and short horizontal line
\rule{0.3\textwidth}{0.4pt}\par % Short horizontal line under the title
\vspace{\drop} % Whitespace between the thin horizontal line and the author name
    
{\Large \textsc{Something}}\par % Author name
    
\vfill
    
\rule{\textwidth}{0.4pt}\par % Thin horizontal line
\vspace{2pt}\vspace{-\baselineskip} % Whitespace between lines
\rule{\textwidth}{1pt}\par % Thick horizontal line
    
\endgroup}
{% endhighlight %}


## Document

{% highlight latex %}
\begin{document}
    
\pagestyle{empty} % Removes page numbers
\titleAT % This command includes the title page
    
\newpage
\tableofcontents
\listoffigures
\listoftables
\newpage
    
\pagestyle{plain}
Dedication
\newpage

\pagestyle{plain}
Acknowledgement
\newpage

\chapter*{\centering Abstract}
\addcontentsline{toc}{chapter}{Abstract}
Write something.

\input{section1.tex}
% or
\section{section1}
\footcite[1]{elder2012practical} % elder2012practical can been seen in references.bib
    
\newpage
\printbibliography
\end{document}
{% endhighlight %}

- It's recommended to use `\input{file.tex}` for a large writing project.
- biblatex's \printbibliography is very convenient.

Another example see [StackExchange](http://tex.stackexchange.com/questions/20538/)

There are many commands we can use in the document. [Dash](http://kapeli.com/dash) has a LaTeX documentation. Here I only list the commands I have used.

### Math Symbols

Math symbols include greek letters `\alpha` $$\alpha$$, `\beta` $$\beta$$, `\chi` $$\chi$$, `\delta` $$\delta$$, `\Delta` $$\Delta$$, `\epsilon` $$\epsilon$$, `\lambda` $$\lambda$$, `\mu` $$\mu$$, `\pi` $$\pi$$, `\rho` $$\rho$$, `\sigma` $$\sigma$$, `\theta` $$\theta$$, `\varepsilon` $$\varepsilon$$, and others: `\approx` $$\approx$$, `\geq` $$\geq$$, `\leq` $$\leq$$, `\neq` $$\neq$$, `\bar{x}` $$\bar{x}$$, `\hat{x}` $$\hat{x}$$, `\frac{a}{b}` $$\frac{a}{b}$$, 'logic and' `\land` $$\land$$, `\ln` $$\ln$$, `\log` $$\log$$, `\mid` $$\mid$$, `\pm` $$\pm$$, `\prod` $$\prod$$, `\sim` $$\sim$$, `\sqrt{3}` $$\sqrt{3}$$, `\sum` $$\sum$$, `\times` $$\times$$, `\lceil` $$\lceil$$, `\lfloor` $$\lfloor$$, `\rceil` $$\rceil$$, `\rfloor` $$\rfloor$$, `\infty` $$\infty$$, `\int_a^b\!f(x)\,\mathrm{d}x`, $$\int_a^b\!f(x)\,\mathrm{d}x$$

Equations, for examples,

{% highlight latex %}
\lim_{x\to a} f(x)=L
{% endhighlight %}

will produce

$$\lim_{x\to a} f(x)=L$$

{% highlight latex %}
\frac{dy}{dx} = \lim_{\Delta x\to 0} \frac{\Delta y}{\Delta x}
{% endhighlight %}

$$\frac{dy}{dx} = \lim_{\Delta x\to 0} \frac{\Delta y}{\Delta x}$$

{% highlight latex %}
\underset{n\rightarrow\infty}{\bar{X}}\sim {\left(\mu, \frac{\sigma^2}{n}\right)}
{% endhighlight %}

$$\underset{n\rightarrow\infty}{\bar{X}}\sim {\left(\mu, \frac{\sigma^2}{n}\right)}$$

{% highlight latex %}
(f \circ g)(x)=f(g(x))
{% endhighlight %}

$$(f \circ g)(x)=f(g(x))$$

{% highlight latex %}
f(X)=\binom{n}{x}\,p^x\,{\left(1-p\right)}^{n-x}
{% endhighlight %}

$$f(X)=\binom{n}{x}\,p^x\,{\left(1-p\right)}^{n-x}$$

More math symbols see [this](http://www.artofproblemsolving.com/Wiki/index.php/LaTeX:Symbols). You can look up at [Detexify](http://detexify.kirelabs.org/classify.html) which is a engine for LaTeX handwritten symbol recognition.

### More on Math Typesetting

{% highlight latex %}
\( and \)
\[ and \]
\bm
\displaystyle
\eqref
\left and \right
\mathbb
\mathnormal
\mathop
\mathrm
{% endhighlight %}

### PGF/TikZ

Common commands are

{% highlight latex %}
\closedcycle
\coordinate
\draw
\empty
\fill
\foreach, \x, \y
\node
\path
{% endhighlight %}

The following are examples:

![alt text](http://i.imgur.com/yYLZ8t5.png "1")

was produced by

{% highlight latex %}
\begin{center}
\begin{tikzpicture}[
block/.style={rectangle,draw,fill=blue!20,text width=6em,text centered,rounded corners,minimum height=4em,node distance=2cm,auto},
line/.style={draw,-latex',node distance= 2cm,auto}]
\node [block] (a) {Real-world problem};
\node [block, right=of a] (b) {Mathematical model};
\node [block, below=of b] (c) {Mathematical conclusions};
\node [block, left=of c] (d) {Real-world predictions};
\path [line] (a) -- node {Formulate}(b);
\path [line] (b) -- node {Solve}(c);
\path [line] (c) -- node {Interpret}(d);
\path [line] (d) -- node {Test}(a);
\end{tikzpicture}
\end{center}
{% endhighlight %}

![alt text](http://i.imgur.com/hkPkI1K.png "2")

was produced by

{% highlight latex %}
\begin{figure}[h]\centering
\subfloat[$y=x^2+x+1$]{\begin{tikzpicture}
    \coordinate (x) at (2,0); \coordinate (y) at (0,3); \draw [<->] (x) node[below] {$x$} -- (0,0) -- (y) node[left] {$y$}; \draw [-] (-2,0) -- (0,0) -- (0,-1);
    \foreach \x in {1} \draw (\x cm,1pt) -- (\x cm,-1pt) node[anchor=north] {$\x$}; \foreach \y in {2} \draw (1pt,\y cm) -- (-1pt,\y cm) node[anchor=east] {$\y$};
    \draw[domain=-2:1] plot (\x, {\x*\x+\x+1});\end{tikzpicture}}
\subfloat[$y=-2x^2+3x+1$]{\begin{tikzpicture}
    \coordinate (x) at (2,0); \coordinate (y) at (0,3); \draw [<->] (x) node[below] {$x$} -- (0,0) -- (y) node[left] {$y$}; \draw [-] (-2,0) -- (0,0) -- (0,-1);
    \foreach \x in {1} \draw (\x cm,1pt) -- (\x cm,-1pt) node[anchor=north] {$\x$}; \foreach \y in {2} \draw (1pt,\y cm) -- (-1pt,\y cm) node[anchor=east] {$\y$};
    \draw[domain=-0.55:2.05] plot (\x, {-2*\x*\x+3*\x+1}); \end{tikzpicture}}\qquad
\subfloat[$y=x^3-x+1$]{\begin{tikzpicture}[scale=0.5]
    \begin{axis}[axis x line=middle,axis y line=middle,domain=-1.5:1.5,samples=100,xlabel=$x$,ylabel=$y$,legend pos=north west,legend style={draw=none, empty legend}]
    \addplot [thick] {x^3-x+1};\legend{}\end{axis}\end{tikzpicture}}
\subfloat[$y=x^4-3x^2+x$]{\begin{tikzpicture}[scale=0.5]
    \begin{axis}[axis x line=middle,axis y line=middle,domain=-2:2,samples=100,xlabel=$x$,ylabel=$y$,legend pos=north west,legend style={draw=none, empty legend}]
    \addplot [thick] {x^4-3*x^2+x};\legend{}\end{axis}\end{tikzpicture}}
\subfloat[$y=3x^5-25x^3+60x$]{\begin{tikzpicture}[scale=0.5]
    \begin{axis}[axis x line=middle,axis y line=middle,domain=-2.5:2.5,samples=100,xlabel=$x$,ylabel=$y$,legend pos=north west,legend style={draw=none, empty legend}]
    \addplot [thick] {3*x^5-25*x^3+60*x};\legend{}\end{axis}\end{tikzpicture}}
\end{figure}
{% endhighlight %}

![alt text](http://i.imgur.com/oXIjG0C.png "3")

was produced by

{% highlight latex %}
\begin{tikzpicture}[scale=.75]
\draw[->,thick] (-8,0) -- (-2,0);
\draw[->,thick] (2,0) -- (8,0);
\draw[->,thick] (-6,0) node[below]{$x$} parabola bend (0,2.5) (6,0) node[below]{$f(x)$};
\draw[->,thick] (-4,0) node[below]{$a$} parabola bend (0,1.5) (4,0) node[below]{$f(a)$};
\node at (0,1) {$f$};
\fill (-6,0) circle[radius=2pt];
\fill (-4,0) circle[radius=2pt];
\end{tikzpicture}
    
\begin{tikzpicture}[scale=.75]
\draw[->,thick] (-8,0) -- (-2,0);
\draw[->,thick] (2,0) -- (8,0);
\draw[->,thick] (-5.5,0) node[above]{$x$} parabola bend (0,2) (5.5,0) node[above]{$f(x)$};
\node at (0,1.5) {$f$};
\foreach \x/\y in {-6/$a-\delta$,-5/$a$,-4/$a+\delta$,4/$L-\varepsilon$,5/$L$,6/$L+\varepsilon$}{
    \node[below] at (\x,0) {\y};
    \fill (\x,0) circle[radius=2pt];
}
\end{tikzpicture}
{% endhighlight %}

![alt text](http://i.imgur.com/4uqMRib.png "4")

was produced by

{% highlight latex %}
\begin{figure}[h]\centering
\subfloat[$f(x)= \frac{x^2-x-2}{x-2}$]{\begin{tikzpicture}[scale=0.5]
    \begin{axis}[axis x line=middle,axis y line=middle,domain=-3:3,samples=100,xlabel=$x$,ylabel=$y$]
    \addplot [thick] {x+1};\addplot[holdot] coordinates{(2,3)};\end{axis}\end{tikzpicture}}
\subfloat[$f(x) = \frac{1}{x^2}$ if $x\neq 0$ \qquad or $1$ if $x=0$]{\begin{tikzpicture}[scale=0.5]
    \begin{axis}[axis x line=middle,axis y line=middle,domain=-0.005:0.005,samples=100,xlabel=$x$,ylabel=$y$]
    \addplot [thick] {1/(x^2)};\addplot[soldot] coordinates{(0,1)};\end{axis}\end{tikzpicture}}
\subfloat[$f(x)=|\floor*{x}|$]{\begin{tikzpicture}[scale=0.5]
    \begin{axis}[axis x line=middle,axis y line=middle,domain=-1.5:4,samples=100,xlabel=$x$,ylabel=$y$]
    \addplot [thick,jump mark left,samples at={-1,0,...,4}] {floor(x)};\foreach \x in {-1,...,3}{\addplot[soldot] coordinates{(\x,\x)};\addplot[holdot] coordinates{(\x+1,\x)};}\end{axis}\end{tikzpicture}}
\end{figure}
{% endhighlight %}

![alt text](http://i.imgur.com/wR4r8OM.png "5")

was produced by

{% highlight latex %}
\begin{figure}[h]\centering
\subfloat[$y=f(x)=\abs{x}$]{\begin{tikzpicture}
    \coordinate (x) at (3,0); \coordinate (y) at (0,3); \draw [<->] (x) node[below] {$x$} -- (0,0) -- (y) node[left] {$y$}; \draw [-] (-3,0) -- (0,0) -- (0,-1);
    \draw[domain=-2.5:0] plot (\x, {-\x});\draw[domain=0:2.5] plot (\x, {\x});\end{tikzpicture}}
\subfloat[$y=f'(x)$]{\begin{tikzpicture}
    \coordinate (x) at (3,0); \coordinate (y) at (0,2); \draw [<->] (x) node[below] {$x$} -- (0,0) -- (y) node[left] {$y$}; \draw [-] (-3,0) -- (0,0) -- (0,-2);
    \foreach \y in {-1,1} \draw (1pt,\y cm) -- (-1pt,\y cm) node[anchor=east] {$\y$};
    \draw[domain=-3:0] plot (\x, {-1});\draw[domain=0:3] plot (\x, {1});\foreach \y in {-1,1} \draw[fill=white] (0,\y) circle[radius=2pt];\end{tikzpicture}}
\end{figure}
{% endhighlight %}

![alt text](http://i.imgur.com/d8z2dK8.png "6")

was produced by

{% highlight latex %}
\begin{center}
\begin{tikzpicture}
\begin{axis}[
	axis x line=bottom,
	axis y line=middle,
	xlabel=$t$, xlabel style={at=(current axis.right of origin), anchor=west},
	ylabel=$y$, ylabel style={at=(current axis.above origin), anchor=south},
	domain=1:6,
	samples=100,
	ymin=0,ymax=7,xmin=0,xmax=7,
	xtick={0,1,4,6},xticklabels={0,a,x,b},ytick=\empty]
\addplot [] {sin(deg(x-0.5))+4} \closedcycle;
\addplot [fill=color1,domain=1:4,samples=100] {sin(deg(x-0.5))+4} \closedcycle;
\end{axis}
\node at (2.5,2) {area = $g(x)$};
\node at (4,4) {$y=f(t)$};
\end{tikzpicture}
\end{center}
{% endhighlight %}

![alt text](http://i.imgur.com/JTaQIgo.png "7")

was produced by

{% highlight latex %}
\begin{center}
\begin{tikzpicture}
\begin{axis}[every axis plot post/.append style={
  mark=none,domain=-2:3,samples=100,smooth}, % All plots: from -2:2, 50 samples, smooth, no marks
axis x line*=bottom, % no box around the plot, only x and y axis
axis y line*=left, % the * suppresses the arrow tips
enlargelimits=upper] % extend the axes a bit to the right and top
\addplot {\gauss{0}{0.5}};
\addplot {\gauss{1}{0.75}};
\end{axis}
\end{tikzpicture}
\end{center}
{% endhighlight %}

![alt text](http://i.imgur.com/qyFP7we.png "8")

was produced by

{% highlight latex %}
\begin{figure}[H]\centering
\caption{Breakdown of the variation of $\Yi$ into two components}
\begin{tikzpicture}
\begin{axis}[
	axis x line=bottom,
	axis y line=middle,
	xlabel=$X$, xlabel style={at=(current axis.right of origin), anchor=west},
	ylabel=$Y$, ylabel style={at=(current axis.above origin), anchor=south},
	domain=0:6,
	samples=100,
	ymin=0,ymax=9,xmin=0,
	xtick={0,3.5},xticklabels={0,$\Xi$},ytick={4},yticklabels={$\bar{Y}$},
	legend pos=north west,legend style={empty legend}]
\addplot [thick] {1.5*x+1};
\addplot [] {4};
\legend{$\Yi=\eb1+\eb2\Xi$}
\end{axis}
\draw [dashed] (4,0) -- (4,5.5);
\draw[fill] (4,5.5) circle[radius=1pt] node[anchor=south] {$\Yi$};
\draw[fill] (4,3.975) circle[radius=1pt];
\node at (4.5,4) {$\ey_i$};
\node at (6.75,5.5) {SRF};
\draw [decorate,decoration={brace,amplitude=5pt},xshift=-2pt,yshift=0pt]
(4,2.6) -- (4,5.5) node [black,midway,xshift=-1.5cm] {\footnotesize $\lyi=(\Yi-\bar{Y})=$ total};
\draw [decorate,decoration={brace,amplitude=5pt,mirror,raise=2pt},yshift=0pt]
(4,4) -- (4,5.5) node [black,midway,xshift=2.5cm] {\footnotesize $\eu_i=$ due to residual};
\draw [decorate,decoration={brace,amplitude=5pt,mirror,raise=2pt},yshift=0pt]
(4,2.6) -- (4,4) node [black,midway,xshift=2.5cm] {\footnotesize ${\hat{y}_i=(\hat{\Yi}-\bar{Y})}=$ due to regression};
\end{tikzpicture}
\end{figure}
{% endhighlight %}

More drawing options and more powerful examples (Python's matplotlib, Matlab, R's ggplot2, Mathematica) see <http://www.zhihu.com/question/21664179>

> 工科生说 Matlab 完爆其他
>
> 数学系的说 Mathematica 高贵冷艳
>
> 统计系的说 R 语言作图领域天下无敌
>
> 计算机系的说 Python 低调奢华有内涵
>
> ......

### Others

{% highlight latex %}
\! and \, and \\
\Aboxed
\addplot
\big, \bigg, \Big, \Bigg
\bottomrule, \cmidrule, \fbox, \midrule, \multicolumn, \toprule
\caption
\cdot, \cdots, \dots, \vdots
\centering
\emph, \textbf
\gauss
\gls, \glsaddall, \makeglossaries, \newglossaryentry, \printglossaries
\hspace
\in
\item
\label
\legend
\longrightarrow, \rightarrow
\mkern
\overline
\qquad
\SI
\text
\widefbox
{% endhighlight %}

### Environments

{% highlight latex %}
\aligned
\align
\enumerate
\empheq
\flalign
\subfloat
{% endhighlight %}

Note that we can put `*` after the environment name to stop numbering.

## Resources

PDFs

- Beamer
    - [A Beamer Tutorial in Beamer](https://www.uncg.edu/cmp/reu/presentations/Charles%20Batts%20-%20Beamer%20Tutorial.pdf)

- Tables
    - [LaTeX Table Hints and Tips](http://nepsweb.co.uk/docs/tableTricks.pdf)
    - [Publication quality tables in LaTeX (booktabs Manual)](http://texdoc.net/texmf-dist/doc/latex/booktabs/booktabs.pdf)
    - [Small Guide to Making Nice Tables (slides)](http://www.inf.ethz.ch/personal/markusp/teaching/guides/guide-tables.pdf)

- TikZ
    - [A Very Minimal Introduction to TikZ](http://cremeronline.com/LaTeX/minimaltikz.pdf)
    - [Commutative Diagrams using TikZ](http://www.felixl.de/commu.pdf)
    - [How to TikZ? - An overview](https://www.coga.tu-berlin.de/fileadmin/i26/download/AG_DiskAlg/FG_KombOptGraphAlg/kappmeier/talks/How_to_TikZ.pdf)
    - [Manual for Package pgfplots](http://pgfplots.sourceforge.net/pgfplots.pdf)
    - - [TikZ and PGF Manual](http://paws.wcu.edu/tsfoguel/tikzpgfmanual.pdf)

- Maths and symbols
    - [Short Math Guide for LaTeX](ftp://ftp.ams.org/pub/tex/doc/amsmath/short-math-guide.pdf)
    - [The Comprehensive LaTeX Symbol List](http://www.tex.ac.uk/tex-archive/info/symbols/comprehensive/symbols-a4.pdf)
    - [The Great, Big List of LaTeX Symbols](https://www.rpi.edu/dept/arc/training/latex/LaTeX_symbols.pdf)

- Others
    - [LaTeX 2ε Cheat Sheet by Stdout.org](http://www.stdout.org/~winston/latex/latexsheet-a4.pdf)
    - [LaTeX Sublime Papers2 Cheat Sheet (For Mac)](http://vaisaghvt.files.wordpress.com/2012/10/sublimelatexsheet-mac.pdf)
    - [Useful LaTeX](http://www.amelialin.com/latex/usefullatex.pdf)

Webpage

- [LaTeX Macros by Wikibooks](http://en.wikibooks.org/wiki/LaTeX/Macros)
- [知乎](http://www.zhihu.com/topic/19568710)


