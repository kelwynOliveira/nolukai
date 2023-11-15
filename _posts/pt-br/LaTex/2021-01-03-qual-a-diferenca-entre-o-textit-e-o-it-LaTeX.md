---
layout: post
lang: pt-BR
title: 'Qual a diferença entre o \textit e o \it - LaTeX'
date: 2021-01-03 18:00:00 -0400
description: "Neste artigo você descobre qual a diferença entre o \\textit e o \\it."
image: "/assets/LaTeX/thumb/thumb-latex-5.jpg"
category: LaTeX
tags: LaTeX
---

Os comandos como `\it`, `\bf` e `\sl` se tornaram obsoletos, ou seja, não suportados pelo esquema de fontes do LaTeX2e.

Isso significa que quando esses comandos são utilizados as atribuições de fontes serão resetadas. É por isso que aninhar esses comandos não vai funcionar muito bem.

```TeX
\documentclass[12pt]{article}
\begin{document}

{ \it \bf Texto } - executa somente negrito

{ \itshape \bfseries Texto } - executa itálico e negrito

{ {\it F}rase } - não há espaçamento entre as letras F e r

{ \textit{F}rase } - há espaçamento entre as letras F e r

\end{document}
```

![Resultado da diferenca entre o textit e o it no LaTeX]({{ "/assets/LaTeX/Qual-a-diferenca-entre-o-textit-e-o-it-LaTeX.jpg" | relative_url }} "Resultado da diferenca entre o textit e o it no LaTeX")

{%- include end_article.html -%}
