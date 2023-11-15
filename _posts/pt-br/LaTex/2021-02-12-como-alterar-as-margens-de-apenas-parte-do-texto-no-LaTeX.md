---
layout: post
lang: pt-BR
title: "Como alterar as margens de apenas parte do texto no LaTeX"
date: 2021-02-12 18:00:00 -0400
description: "Neste artigo você descobre como alterar as margens de apenas parte do texto no LaTeX."
image: "/assets/LaTeX/thumb/thumb-latex-7.jpg"
category: LaTeX
tags: LaTeX
---

Em alguns trabalhos você pode querer alterar as margens de uma determinada página, as margens de um determinado parágrafo ou mesmo de uma seção inteira. Neste artigo você descobre como alterar as margens de apenas parte do texto em seu documento LaTeX.

A opção mais simples é utilizar o pacote **changepage** (<a href="https://www.ctan.org/pkg/changepage" target="_blank">documentação</a>). Com este pacote você poderá utilizar o ambiente **adjustwidth**:

```TeX
\begin{adjustwidth}{margem esquerda}{margem direita}
   Conteúdo
\end{adjustwidth}
```

O ambiente **quotation** é similar à:

```TeX
\documentclass[12pt]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage[strict]{changepage}
\usepackage{lipsum}

\begin{document}
    \lipsum[1]
    \begin{adjustwidth}{2.5em}{2.5em}
        \lipsum[1]
    \end{adjustwidth}
    \lipsum[1]
\end{document}
```

Caso queira que a margem cresça é só inserir valores negativos.

Para a margem apenas em um dos lados é só deixar as chaves do lado que se deseja manter em branco. Por exemplo, alterar apenas a margem direita:

```TeX
\begin{adjustwidth}{}{-1cm}
   Conteúdo
\end{adjustwidth}
```

<br>

{%- include end_article.html -%}
