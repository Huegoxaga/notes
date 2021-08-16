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
- `${x_1}_2$` ![${x_1}_2$](https://render.githubusercontent.com/render/math?math=%24%7Bx_1%7D_2%24) subscript of a subscript
- `$\pi$` ![$\pi](https://render.githubusercontent.com/render/math?math=%24%5Cpi) greek letters
- `$A=\pi r^2$` ![$A=\pi r^2$](https://render.githubusercontent.com/render/math?math=%24A%3D%5Cpi%20r%5E2%24) greek letter need to have a space with others.
- `$\sin{x}$` ![$\sin{x}$](https://render.githubusercontent.com/render/math?math=%24%5Csin%7Bx%7D%24) trig functions
- `$\tan^{-1}{x}$` ![$\tan^{-1}{x}$](https://render.githubusercontent.com/render/math?math=%24%5Ctan%5E%7B-1%7D%7Bx%7D%24) trig functions with exponent
- `$\log{x}$` ![$\log{x}$](https://render.githubusercontent.com/render/math?math=%24%5Clog%7Bx%7D%24) log functions
- `$\log_5{x}$` ![$\log_5{x}$](https://render.githubusercontent.com/render/math?math=%24%5Clog_5%7Bx%7D%24) log function with a base
- `$\ln{x}$` ![$\ln{x}$](https://render.githubusercontent.com/render/math?math=%24%5Cln%7Bx%7D%24) nature log function
- `$\sqrt{2}$` ![$\sqrt{2}$](https://render.githubusercontent.com/render/math?math=%24%5Csqrt%7B2%7D%24) square root
- `$\sqrt[3]{2}$` ![$\sqrt{3}{2}$](https://render.githubusercontent.com/render/math?math=%24%5Csqrt%7B3%7D%7B2%7D%24) cubic root
- `$\sqrt[3]{1+\sqrt{x}}$` ![$\sqrt{3}{1+\sqrt{x}}$](https://render.githubusercontent.com/render/math?math=%24%5Csqrt%7B3%7D%7B1%2B%5Csqrt%7Bx%7D%7D%24) square root of a cubic root
- `$\frac{1}{3}$` ![$\frac{1}{3}$](https://render.githubusercontent.com/render/math?math=%24%5Cfrac%7B1%7D%7B3%7D%24) fraction
- `$(x+1)$` ![$(x+1)$](https://render.githubusercontent.com/render/math?math=%24(x%2B1%29%24) parentheses
- `$|x|$` ![$|x|$](https://render.githubusercontent.com/render/math?math=%24%7Cx%7C%24) absolute value
- `$\left(\frac{2}{3}\right)$` ![$\left(\frac{2}{3}\right)$](https://render.githubusercontent.com/render/math?math=%24%5Cleft(%5Cfrac%7B2%7D%7B3%7D%5Cright%29%24) expand the brackets, otherwise it looks like this
- `$\left(\frac{2}{3}\right.$` ![$\left(\frac{2}{3}\right.$](https://render.githubusercontent.com/render/math?math=%24%5Cleft(%5Cfrac%7B2%7D%7B3%7D%5Cright.%24) show only the left bracket.
- `$[x+1]$` ![$[x+1]$](https://render.githubusercontent.com/render/math?math=%24%5Bx%2B1%5D%24) square bracket
- `$\{x,y,z\}$` ![${x,y,z}$](https://render.githubusercontent.com/render/math?math=%24%5C%7Bx%2Cy%2Cz%5C%7D%24) curly brackets need to be escaped by `\`
- `$\$88.88$` ![$$88.88$](https://render.githubusercontent.com/render/math?math=%24%5C%2488.88%24) escape dollar sign
- `$\sum_{n=0}^{\infty}$` ![$\sum_{n=0}^{\infty}$](https://render.githubusercontent.com/render/math?math=%24%5Csum_%7Bn%3D0%7D%5E%7B%5Cinfty%7D%24) sigma sum
- `$\int_a^b$` ![$\int_a^b$](https://render.githubusercontent.com/render/math?math=%24%5Cint_a%5Eb%24) integral
- `$\lim_{x \to a}$` ![$\lim_{x \to a}$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%7D%24) limit
- `$\lim_{x \to a^+} f(x)$` ![$\lim_{x \to a^+} f(x)$](https://render.githubusercontent.com/render/math?math=%24%5Clim_%7Bx%20%5Cto%20a%5E%2B%7D%20f(x%29%24) limit
- `$f'(a)$` ![$f'(a)$](https://render.githubusercontent.com/render/math?math=%24f'(a%29%24) derivative
- `$\binom{n}{k} = \frac{n!}{k!(n-k)!}$` binomial
- `$\begin{matrix} a & b \\ c & d \end{matrix}$` ![$\begin{matrix} a & b \ c & d \end{matrix}$](https://render.githubusercontent.com/render/math?math=%24%5Cbegin%7Bmatrix%7D%20a%20%26%20b%20%5C%5C%20c%20%26%20d%20%5Cend%7Bmatrix%7D%24) matrix without brackets
- `$\begin{pmatrix} a & b \\ c & d \end{pmatrix}$` ![$\begin{pmatrix} a & b \ c & d \end{pmatrix}$](https://render.githubusercontent.com/render/math?math=%24%5Cbegin%7Bpmatrix%7D%20a%20%26%20b%20%5C%5C%20c%20%26%20d%20%5Cend%7Bpmatrix%7D%24) matrix with round brackets
- `$\begin{bmatrix} 1 & 2 & 1 \\ 3 & 0 & 1 \\ 0 & 2 & 4 \end{bmatrix}$` ![$\begin{bmatrix} 1 & 2 & 1 \ 3 & 0 & 1 \ 0 & 2 & 4 \end{bmatrix}$](https://render.githubusercontent.com/render/math?math=%24%5Cbegin%7Bbmatrix%7D%201%20%26%202%20%26%201%20%5C%5C%203%20%26%200%20%26%201%20%5C%5C%200%20%26%202%20%26%204%20%5Cend%7Bbmatrix%7D%24) matrix with square brackets
- `$\left[ \begin{array}{cc|r} 3 & 4 & 5 \\ 1 & 3 & 729 \end{array} \right]$` ![$\left[ \begin{array}{cc|r} 3 & 4 & 5 \ 1 & 3 & 729 \end{array} \right]$](https://render.githubusercontent.com/render/math?math=%24%5Cleft%5B%20%5Cbegin%7Barray%7D%7Bcc%7Cr%7D%203%20%26%204%20%26%205%20%5C%5C%201%20%26%203%20%26%20729%20%5Cend%7Barray%7D%20%5Cright%5D%24) Augmented Matrix
- `$\left | \begin{matrix} a_11 - \lambda & a_12 \\ a_21 & a_22 - \lambda \end{matrix} \right | $` ![$\left | \begin{matrix} a_11 - \lambda & a_12 \ a_21 & a_22 - \lambda \end{matrix} \right | $](https://render.githubusercontent.com/render/math?math=%24%5Cleft+%7C+%5Cbegin%7Bmatrix%7D+a_11+-+%5Clambda+%26+a_12+%5C%5C+a_21+%26+a_22+-+%5Clambda+%5Cend%7Bmatrix%7D+%5Cright+%7C+%24) Determinant of a matrix.

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
