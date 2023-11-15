---
layout: post
lang: pt-BR
title: "Como colorir e sublinhar links com hyperref no LaTeX"
date: 2021-02-14 18:00:00 -0400
description: "Neste artigo você descobre como colorir e sublinhar links com hyperref no LaTeX."
image: "/assets/LaTeX/thumb/thumb-latex-1.jpg"
category: LaTeX
tags: LaTeX
---

Por padrão quando você habilita o colorlinks o hyperref (<a href="https://www.ctan.org/pkg/hyperref" target="_blank\">documentação</a>) desabilita a caixa que fica ao redor do link no LaTeX.

O código utilizado para colorir e sublinhar links pode ser:

```TeX
\documentclass[12pt]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage{xcolor}
\definecolor{eea}{HTML}{7A29F2}

\usepackage{hyperref}

\hypersetup{ %
colorlinks=true,%
linkcolor=eea,%
linkbordercolor=red,%
}
\makeatletter
\Hy@AtBeginDocument{ %
\def\@pdfborder{0 0 1}%
\def\@pdfborderstyle{/S/U/W 2}%
}
\makeatother

\begin{document}

\section{Título}\label{sec:secao}

[...]

Este é o link da \hyperref[sec:secao]{seção}.

\end{document}
```

Em **\hypersetup** definimos o estilo para os links.

- **colorlink=true** diz que os links serão coloridos;
- **linkcolor=eea** define a cor para o link que foi criada com **\definecolor{eea}{HTML}{7A29F2}**;
- **linkbordercolor=red** define a cor vermelha como cor das linhas de borda ao redor do link.

Já dentro de **\Hy@AtBeginDocument** definimos:

- **\@pdfborder{0 0 1}** para substituir a definição de não criação de borda que é gerada ao informar colorlink=true. Dessa forma a borda é mantida.
- **\def\@pdfborderstyle{/S/U/W 2}** para substituir o estilo da borda dizendo que invés de ser uma caixa é apenas uma linha abaixo do link (underline/sublinhado) com espessura de 2pt.

{%- include end_article.html -%}
