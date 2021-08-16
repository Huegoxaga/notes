# LaTeX

## Introduction

- LaTeX is a typesetting language for producing scientific documents.
- Jupyter notebook recognizes LaTeX code written in markdown cells and renders the symbols in the browser using the MathJax JavaScript library.
- LaTex has sereval distributions for different operation system. A LeTeX distribution compiles code into text.
  - [MacTeX](http://www.tug.org/mactex/) distribution for macOS
  - [MiKTeX](https://miktex.org) distribution for Window
- LaTex source code has extension as `tex`
- Online editting tool can be used to write and compile LaTex Code quickly.
  - [Overleaf](https://www.overleaf.com)
- LaTeX works with editors as follow:
  - TeXworks - included in distributions.
  - Texmaker
- LaTex text document can be compiled as `.dvi`(Device independent file format) or be compiled by `pdflatex` as `.pdf` or converted from `.dvi` to `.pdf` by using `dvi2pdf`.
- Jupyter notebook recognizes LaTeX code written in markdown cells and renders the symbols in the browser using the MathJax JavaScript library.
- LaTeX works well with bibliography management packages like biblatex to generated auto formatted article references.
  - It has a extension as `.bib`.
  - It works well with bibliography management systems(softwares) like [JabRef](http://www.jabref.org) and [BibDesk](https://sourceforge.net/p/bibdesk/svn/HEAD/tree/)(Mac Only)

## Syntax

### Document Formatting

- title

```
\documentclass[12pt, letterpaper, twoside]{article}
\usepackage[utf8]{inputenc}

\title{First document}
\author{Hubert Farnsworth \thanks{funded by the Overleaf team}}
\date{February 2014}

\begin{document}

\begin{titlepage}
\maketitle
\end{titlepage}

In this document some extra packages and parameters
were added. There is an encoding package
and pagesize and fontsize parameters.

\end{document}
```

- abstract

```
\documentclass[12pt, letterpaper, twoside]{article}
\usepackage[utf8]{inputenc}

\begin{document}

\begin{abstract}
This is a simple paragraph at the beginning of the document. A brief introduction to the main subject.
\end{abstract}

In this document some extra packages and parameters
were added. There is an encoding package,
and pagesize and fontsize parameters.

This line will start a second paragraph. And I can
 break\\ the lines \\ and continue on a new line.

\end{document}
```

- comment

```
\documentclass{article}
\usepackage[utf8]{inputenc} %codification of the document

\usepackage{comment}

%Here begins the body of the document
\begin{document}
This document contains a lot of comments, none of them
will appear here, only this text.

This document contains a lot of comments, none of them
will appear here, only this text.

\begin{comment}
This text won't show up in the compiled pdf
this is just a multi-line comment. Useful
to, for instance, comment out slow-rendering parts
while working on a draft.
\end{comment}

\end{document}
```

- New Line
  - One extra empty line will place text in a new line.
  - Use `\\`

### Text Styles

- `\textit{text}` italic
- `\textbf{text}` bold
- `\textsc{text}` small captalized
- `\texttt{text}` typewriter font
- `\begin(large)text\end(large)` large font size
- `\begin(Large)text\end(Large)` very large font size
- `\begin(huge)text\end(huge)` huge font size
- `\begin(Huge)text\end(Huge)` very huge font size
- `\begin(small)text\end(small)` small font size
- `\begin(tiny)text\end(tiny)` tiny font size
- `\begin(center)text\end(center)` centered
- `\begin(flushleft)text\end(flushleft)` left-justified
- `\begin(flushright)text\end(flushright)` right-justified

### Mathematics

##### Mathematical Modes

- inline mode - inline math expression as part of a text
  - use delimiters: `\( \)`, `$ $` or `\begin{math} \end{math}`
- display mode - centered math expression in a new paragraph.
  - use delimiters: `\[ \]`, `$$ $$`, `\begin{displaymath} \end{displaymath}` or `\begin{equation} \end{equation}`

##### Symbol Size

- `$\displaystyle{x}$` normal size for math symbols and expressions.
- or replace `\display` with `\large`, `\Large`, `\LARGE`, `\huge`, `\Huge` to make the math object even bigger.

##### Spacing

- LaTeX provides the following four commands for spacing in math mode:
  - `\;` - a thick space.
  - `\:` - a medium space.
  - `\,` - a thin space.
  - `\!` - a negative thin space.

##### Common Math Symbols

- `\times` multiply
- `\approx` approximate
- `\pm` plus minus
- `\cdot` dot for multiplication
- `\neq` not equal

##### Math Expressions

- Use [Detexify](http://detexify.kirelabs.org/classify.html) to draw a symbol and find the LeTaX syntax for it.
- `\` can be used to escape special symbols used by the compiler.
- `$3x^2$` $$3x^2$$
- `$3x^{3x^2+1}$` $$3x^{3x^2+1}$$ superscripts for more than 1 character
- `$x_1$` $$x_1$$ subscripts
- `${x_1}_2$` $${x_1}_2$$ subscript of a subscript
- `$\pi$` $$\pi$$ greek letters
- `$A=\pi r^2$` $$A=\pi r^2$$ greek letter need to have a space with others.
- `$\sin{x}$` $$\sin{x}$$ trig functions
- `$\tan^{-1}{x}$` $$\tan^{-1}{x}$$ trig functions with exponent
- `$\log{x}$` $$\log{x}$$ log functions
- `$\log_5{x}$` $$\log_5{x}$$ log function with a base
- `$\ln{x}$` $$\ln{x}$$ nature log function
- `$\sqrt{2}$` $$\sqrt{2}$$ square root
- `$\sqrt[3]{2}$` $$\sqrt[3]{2}$$ cubic root
- `$\sqrt[3]{1+\sqrt{x}}$` $$\sqrt[3]{1+\sqrt{x}}$$ square root of a cubic root
- `$\frac{1}{3}$` $$\frac{1}{3}$$ fraction
- `$(x+1)$` $$(x+1)$$ parentheses
- `$|x|$` $$|x|$$ absolute value
- `$\left(\frac{2}{3}\right)$` $$\left(\frac{2}{3}\right)$$ expand the brackets, otherwise it looks like this
- `$\left(\frac{2}{3}\right.$` $$\left(\frac{2}{3}\right.$$ show only the left bracket.
- `$[x+1]$` $$[x+1]$$ square bracket
- `$\{x,y,z\}$` $$\{x,y,z\}$$ curly brackets need to be escaped by `\`
- `$\$88.88$` $$\$88.88$$ escape dollar sign
- `$\sum_{n=0}^{\infty}$` $$\sum_{n=0}^{\infty}$$ sigma sum
- `$\int_a^b$` $$\int_a^b$$ integral
- `$\lim_{x \to a}$` $$\lim_{x \to a}$$ limit
- `$\lim_{x \to a^+} f(x)$` $$\lim_{x \to a^+} f(x)$$ limit
- `$f'(a)$` $$f'(a)$$ derivative
- `$\binom{n}{k} = \frac{n!}{k!(n-k)!}$` $$\binom{n}{k} = \frac{n!}{k!(n-k)!}$$ binomial
- `$\begin{matrix} a & b \\ c & d \end{matrix}$` $$\begin{matrix} a & b \\ c & d \end{matrix}$$ matrix without brackets
- `$\begin{pmatrix} a & b \\ c & d \end{pmatrix}$` $$\begin{pmatrix} a & b \\ c & d \end{pmatrix}$$ matrix with round brackets
- `$\begin{bmatrix} 1 & 2 & 1 \\ 3 & 0 & 1 \\ 0 & 2 & 4 \end{bmatrix}$` $$\begin{bmatrix} 1 & 2 & 1 \\ 3 & 0 & 1 \\ 0 & 2 & 4 \end{bmatrix}$$ matrix with square brackets
- `$\left[ \begin{array}{cc|r} 3 & 4 & 5 \\ 1 & 3 & 729 \end{array} \right]$` $$\left[ \begin{array}{cc|r} 3 & 4 & 5 \\ 1 & 3 & 729 \end{array} \right]$$ Augmented Matrix
- `$\left | \begin{matrix} a_11 - \lambda & a_12 \\ a_21 & a_22 - \lambda \end{matrix} \right | $` $$\left | \begin{matrix} a_11 - \lambda & a_12 \\ a_21 & a_22 - \lambda \end{matrix} \right | $$ Determinant of a matrix.

### Block Contents

##### Tables

```
\begin{tabular}{ |c|c|c| }
 \hline
 $x$ & 1 & 2 \\ \hline
 $2x$ & 2 & 4 \\ \hline
 $3x$ & 3 & 6 \\ \hline
 \hline
\end{tabular}
```

- Each `c` represent a centered column
- Use `|` to define vertical border
- Use `\\` to separate rows
- Use `\hline` to define horizontal border
- Space between `&` is not mandatory

##### Equation Array

```
\begin{eqnarray}
5x^2-9&=&x+3\\
4x^2&=&12\\
x^3&=&3
x&\approx&\pm1.732
\end{eqnarray}
```

- Anything in the equation array is math mode by default.
- Add `*` after `eqnarray` to remove equation numbering.

##### List

```
\begin{enumerate}
\item item1
\item item1
  \begin{enumerate}
  \item subitem1
  \item subitem2
  \end{enumerate}
\item
\end{enumerate}
```

- The example shows a auto numbered list and a list within a list.
- Add `[itemname]` after `\item` to specify item name for display instead of numbers.
- Use `itemize` instead of `enumerate` for bullet list.
