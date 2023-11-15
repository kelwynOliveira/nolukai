---
layout: post
lang: pt-BR
title: "Como alterar o tamanho da fonte dos títulos no LaTeX"
date: 2020-11-12 18:00:00 -0400
description: "Neste artigo você descobre como alterar o tamanho da fonte dos títulos no LaTeX."
image: "/assets/LaTeX/thumb/thumb-latex-5.jpg"
category: LaTeX
tags: LaTeX
---

Pode ser que o tamanho atual da fonte dos títulos não satisfaça você, mas não se preocupe, alterar isso é bem simples. Neste artigo você descobre duas formas.

## Com o pacote titlesec

O código abaixo faz uso do pacote `titlesec` e do comando `\titleformat\*{hierarquia}{formatação}`.

```TeX
\documentclass{article}
\usepackage{titlesec}
\titleformat*{\section}{\Huge\bfseries}
\titleformat*{\subsection}{\LARGE\bfseries}
\titleformat*{\subsubsection}{\LARGE\bfseries}
\titleformat*{\paragraph}{\huge\bfseries}
\titleformat*{\subparagraph}{\huge\bfseries}

\begin{document}
  \section{Seção}
  \subsection{Subseção}
  \subsubsection{Sub-subseção}
  \paragraph{Parágrafo}
  \subparagraph{Subparágrafo}
\end{document}
```

![resultado da alteração do tamanho da fonte dos títulos no LaTeX]({{ "/assets/LaTeX/alteraracao-do-tamanho-da-fonte-dos-titulos-no-LaTeX.jpg" | relative_url }} "resultado da alteração do tamanho da fonte dos títulos no LaTeX")

O `\titlesec*` é a versão simplificada, se você quiser fazer modificações mais \"significativas\" utilize o comando `\titlesec{hierarquia}[forma]{formato}{label}{separação}{antes do código}[depois do código]`. (<a href="https://www.ctan.org/pkg/titlesec" target="\_blank\">veja a documentação do pacote</a>)

## Alteração dos tamanhos com o pacote sectsty

Abaixo está o código para obter o mesmo resultado, mas com o pacote `sectsty`. O comando para alterar a fonte do texto começa com a hierarquia terminado por font:

```TeX
\documentclass{article}
\usepackage{sectsty}
\sectionfont{\Huge}
\subsectionfont{\LARGE}
\subsubsectionfont{\LARGE}
\paragraphfont{\huge}
\subparagraphfont{\huge}

\begin{document}
  \section{Seção}
  \subsection{Subseção}
  \subsubsection{Sub-subseção}
  \paragraph{Parágrafo}
  \subparagraph{Subparágrafo}
\end{document}
```

![resultado da alteração do tamanho da fonte dos títulos no LaTeX]({{ "/assets/LaTeX/alteraracao-do-tamanho-da-fonte-dos-titulos-no-LaTeX.jpg" | relative_url }} "resultado da alteração do tamanho da fonte dos títulos no LaTeX")

{%- include end_article.html -%}
