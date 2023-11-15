---
layout: post
lang: pt-BR
title: "Como adicionar um nível extra de seções abaixo de \\subsubsection - LaTeX"
date: 2020-09-05 18:00:00 -0400
description: "Neste artigo você descobre como adicionar um nível extra de seções abaixo de \\subsubsection no LaTeX"
image: "/assets/LaTeX/thumb/thumb-latex-7.jpg"
category: LaTeX
tags: LaTeX
---

A hierarquia abaixo de `\subsubsection` é o `\paragraph` que possui nível 4. Os níveis de hierarquia dos documentos em LaTeX são divididos como:

| Nível | Hierarquia     |
| ----- | -------------- |
| -1    | \part          |
| 0     | \chapter       |
| 1     | \section       |
| 2     | \subsection    |
| 3     | \subsubsection |
| 4     | \paragraph     |
| 5     | \subparagraph  |

> **_Obs.:_** para a classe article não existe `\chapter`, além disso `\part` se torna nível 0

Contudo o texto dentro da hierarquia **paragraph** fica ao lado do título. Para que o `\paragraph` funcione como uma seção utilize o pacote **titlesec** e configure o seu formato.

```TeX
\documentclass[12pt]{article}
\usepackage{titlesec}
\titleformat{\paragraph}{\normalfont\normalsize\bfseries}{\theparagraph}{1em}{}
\titlespacing*{\paragraph}{0pt}{3.25ex plus 1ex minus .2ex}{1.5ex plus .2ex}
\setcounter{secnumdepth}{4} % numeração até o nível 4
\setcounter{tocdepth}{4} % sumário até o nível 4

\begin{document}
\tableofcontents

\section{Seção}
Texto

\subsection{Subseção}
Texto

\subsubsection{Subsubseção}
Texto

\paragraph{Parágrafo}
Texto

\end{document}
```

![Inclusão de nível abaixo de subsection no LaTeX]({{ "/assets/LaTeX/add-nivel-abaixo-de-subsubsection-1.jpg" | relative_url }} "Inclusão de nível abaixo de subsection no LaTeX")

Caso a sua intenção seja criar uma hierarquia entre `\subsubsection` e `\paragraph` utilize o código abaixo. Ela apresenta a criação de uma **subsubsubsection** de nível 4, alterando os níveis de **paragraph** para 5 e **subparagraph** para 6.

```TeX
\documentclass[12pt]{article}%{standalone}%
%\usepackage[papersize={10cm,4cm}, margin=1cm]{geometry}
%\usepackage{graphicx}
\usepackage{titlesec}
\titleclass{\subsubsubsection}{straight}[\subsection]
\newcounter{subsubsubsection}[subsubsection]
\renewcommand\thesubsubsubsection{\thesubsubsection.\arabic{subsubsubsection}}
\renewcommand\theparagraph{\thesubsubsubsection.\arabic{paragraph}} % Caso queira que paragraph seja numerado
\titleformat{\subsubsubsection}{\normalfont\normalsize\bfseries}{\thesubsubsubsection}{1em}{}
\titlespacing*{\subsubsubsection}{0pt}{3.25ex plus 1ex minus .2ex}{1.5ex plus .2ex}\makeatletter
\renewcommand\paragraph{\@startsection{paragraph}{5}{\z@}{3.25ex \@plus1ex \@minus.2ex}{-1em}{\normalfont\normalsize\bfseries}}
\renewcommand\subparagraph{\@startsection{subparagraph}{6}{\parindent}{3.25ex \@plus1ex \@minus .2ex}{-1em}{\normalfont\normalsize\bfseries}} %nível no sumário

\def\toclevel@subsubsubsection{4}
\def\toclevel@paragraph{5}
\def\toclevel@paragraph{6}%espaçamento no sumário
\def\l@subsubsubsection{\@dottedtocline{4}{7em}{4em}}
\def\l@paragraph{\@dottedtocline{5}{10em}{5em}}
\def\l@subparagraph{\@dottedtocline{6}{14em}{6em}}

\makeatother\setcounter{secnumdepth}{4} % numeração até o nível 4
\setcounter{tocdepth}{4} % sumário até o nível 4

\begin{document}
\tableofcontents

\section{Seção}
Texto

\subsection{Subseção}
Texto

\subsubsection{Subsubseção}
Texto

\subsubsubsection{Subsubsubseção}
Texto

\paragraph{Parágrafo}
Texto

\end{document}
```

![Inclusão de nível abaixo de subsection no LaTeX]({{ "/assets/LaTeX/add-nivel-de-secao-abaixo-de-subsubsection-1.jpg" | relative_url }} "Inclusão de nível abaixo de subsection no LaTeX")

{%- include end_article.html -%}
