---
layout: post
lang: pt-BR
title: "Como ignorar citações em legendas na lista de figuras - LaTeX"
date: 2021-09-10 18:00:00 -0400
description: "Neste artigo você descobre como ignorar citações em legendas na lista de figuras no LaTeX."
image: "/assets/LaTeX/thumb/thumb-latex-5.jpg"
category: LaTeX
tags: LaTeX
---

A solução para que a sua lista de figuras ignore citações em legendas no seu documento LaTeX pode ser mais simples do que você imagina.

Acontece que o comando **caption** possui um parâmetro opcional justamente para especificar o texto que deve ser apresentado na lista de figuras.

```TeX
\caption[legenda que aparece na lista]{legenda que aparece no documento}
```

Veja o exemplo abaixo:

```TeX
\documentclass[12pt,a4paper]{article}
\usepackage[brazil]{babel}
\usepackage{graphicx}
\usepackage{lipsum}

\begin{document}
\listoffigures
\section{Seção}
\lipsum[1]
\cite{B21,A21}.

\begin{figure}[!h]
    \centering
    \includegraphics[width=.5\linewidth]{example-image-a}
    \caption[legenda da figura]{Legenda da figura \cite{B21}}
    \label{fig:marcador}
\end{figure}

\begin{thebibliography}{9}
    \bibitem{B21} A. Silva, \textit{Meu livro fictício sobre
    bibliografia}, 2021.
    \bibitem{A21} B. Oliveira, \textit{Meu artigo fictício
    sobre bibliografia}, 2021.
\end{thebibliography}
\end{document}
```

![Página da lista de figuras sem a citação]({{ "/assets/LaTeX/lista-de-figura-sem-a-citacao.jpg" | relative_url }} "Página da lista de figuras sem a citação")

{%- include end_article.html -%}
