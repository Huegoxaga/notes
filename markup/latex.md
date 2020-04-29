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

#### Document Formatting

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

### Mathematics

##### Mathematical modes

- inline mode - inline math expression as part of a text
  - use delimiters: `\( \)`, `$ $` or `\begin{math} \end{math}`
- display mode - centered math expression in a new paragraph.
  - use delimiters: `\[ \]`, `$$ $$`, `\begin{displaymath} \end{displaymath}` or `\begin{equation} \end{equation}`

##### Math Symbols

- Use [Detexify](http://detexify.kirelabs.org/classify.html) to draw a symbol and find the LeTaX syntax for it.
