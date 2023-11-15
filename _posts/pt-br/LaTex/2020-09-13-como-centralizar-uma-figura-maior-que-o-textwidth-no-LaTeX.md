---
layout: post
lang: pt-BR
title: "Como centralizar uma figura maior que o textwidth no LaTeX"
date: 2020-09-13 18:00:00 -0400
description: "Neste artigo você descobre como centralizar uma figura maior que o textwidth no LaTeX."
image: "/assets/LaTeX/thumb/thumb-latex-1.jpg"
category: LaTeX
tags: LaTeX
---

É possível que em alguns trabalhos você queira que uma figura ultrapasse a largura da área de texto que você definiu.

Normalmente figuras muito grandes se alinham com a margem esquerda do seu documento ultrapassando apenas a margem direita, o que torna impossível alinhar ao centro.

## Centralizando com **makebox**

Caso você queira que a imagem ultrapasse as duas margens de forma que ela fique centralizada no seu documento utilize o comando **\makebox[largura da caixa][alinhamento]{figura}**.

Este comando cria uma caixa e permite realizar o alinhamento na esquerda (parâmetro l), centro (parâmetro c) e direita (parâmetro r).

O parâmetro de alinhamento deve ser informado entre as chaves e o **\incudegraphics** deve ser informado entre as chaves. Tudo isso dentro do ambiente flutuante **figura**. Veja o código abaixo:

```TeX
\documentclass{article}
\usepackage[brazil]{babel}
\usepackage{graphicx}
\usepackage{lipsum}

\begin{document}
\section{Título da seção}

\lipsum[1][1-3]

\begin{figure}[!ht]
  \makebox[\textwidth][c]{\includegraphics[width=1.2\textwidth]{example-image-a}}
  \caption{Legenda}
  \label{fig:marcador}
\end{figure}

\lipsum[1]
\end{document}
```

![Imagem maior que o textwidth está centralizada.]({{ "/assets/LaTeX/imagem-maior-que-o-textwidth-cntralizada.jpg" | relative_url }} "Imagem maior que o textwidth está centralizada.")

## Centralizando com **adjustbox**

O pacote **adjustbox** a partir de 13/08/2011 permite ajustar o alinhamento com left (esquerda), center (centro) e right (direita). Veja o código abaixo:

```TeX
\documentclass{article}
\usepackage[brazil]{babel}
\usepackage[export]{adjustbox}[2011/08/13]
\usepackage{graphicx}
\usepackage{lipsum}\begin{document}
\section{Título da seção}
\lipsum[1][1-3]\begin{figure}[!ht]
  \includegraphics[width=1.2\textwidth,center]{example-image-a}%
  \caption{Legenda}
  \label{fig:marcador}
\end{figure}\lipsum[1]\end{document}
```

![Imagem maior que o textwidth está centralizada.]({{ "/assets/LaTeX/imagem-maior-que-o-textwidth-cntralizada.jpg" | relative_url }} "Imagem maior que o textwidth está centralizada.")

{%- include end_article.html -%}
