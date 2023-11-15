---
layout: post
lang: pt-BR
title: "Como mostrar sub-subseções e parágrafos no sumário com LaTeX"
date: 2020-12-06 18:00:00 -0400
description: "Neste artigo você descobre como mostrar sub-subseções e parágrafos no sumário com LaTeX."
image: "/assets/LaTeX/thumb/thumb-latex-3.jpg"
category: LaTeX
tags: LaTeX
---

Provavelmente você chegou neste artigo porque percebeu que as sub-subseções não aparecem no sumário do seu documento.

Para fazer com que isso aconteça é bem simples. A resposta é que você precisa aumentar o nível do ToC (Table of Contents) da classe de documento que você está utilizando.

Os níveis de hierarquia dos documentos em LaTeX são divididos como:

| Nível | Hierarquia     |
| ----- | -------------- |
| -1    | \part          |
| 0     | \chapter       |
| 1     | \section       |
| 2     | \subsection    |
| 3     | \subsubsection |
| 4     | \paragraph     |
| 5     | \subparagraph  |

> **_Obs.:_** para a classe article não existe `\chapter`, além diosso `\part` se torna nível 0

Normalmente o nível do ToC vai até o nível 2 - subsection. Para configurarmos o nível de profundidade do ToC utilizamos o comando `\setcounter{tocdepth}{nível}`.

Para que haja numeração você deve utilizar o comando `\setcounter{secnumdepth}{nível}`.

No exemplo abaixo o sumário apresenta até o nível 5 (subparagraph) e as hierarquias são numeradas até o nível 4 (paragraph):

```TeX
\documentclass[12pt]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage{lipsum}
\setcounter{tocdepth}{5}
\setcounter{secnumdepth}{4}

\begin{document}
   \tableofcontents

   \part{primeira parte}
   \section{seção}
   \lipsum[1][1]

   \subsection{subseção}
   \lipsum[1][1]

   \subsubsection{subsubseção}
   \lipsum[1][1]

   \paragraph{paragrafo}
   \lipsum[1][1]

   \subparagraph{subparágrafo}
   \lipsum[1][1]
\end{document}
```

![Como mostra sub subseções e parágrafos no sumário com LaTeX]({{ "/assets/LaTeX/Como-mostra-sub-subsecoes-e-paragrafos-no-sumario-com-LaTeX.jpg" | relative_url }} "Como mostra sub subseções e parágrafos no sumário com LaTeX")

{%- include end_article.html -%}
