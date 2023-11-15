---
layout: post
lang: pt-BR
title: "Como colocar duas tabelas lado a lado no LaTeX"
date: 2020-10-31 18:00:00 -0400
description: "Neste artigo você descobre como colocar duas tabelas lado a lado no LaTeX."
image: "/assets/LaTeX/thumb/thumb-latex-5.jpg"
category: LaTeX
tags: LaTeX
---

Existem várias formas de se colocar uma tabela lado a lado no LaTeX.

A forma mais simples de se fazer isso é não utilizando um ambiente flutuante para envolver as tabelas em um ambiente flutuante (
table\*\*).

Codificamos as tabelas sem quebra de linha. Abaixo elas são separadas na horizontal com o comando **\quad**. (<a href="https://estudantesemapuros.com/quais-os-comandos-para-espacamento-horizontal-no-latex/" target="_blank">Quais os comandos para espaçamento horizontal no LaTeX</a>)

```TeX
\documentclass[12pt]{article}

\begin{document}
\centering
\begin{tabular}{|c|c|c|}
    \hline
    a11 & a12 & a13\\
    \hline
    a21 & a22 & a23\\
    \hline
    a31 & a32 & a33\\
    \hline
\end{tabular}
\quad
\begin{tabular}{|c|c|c|}
    \hline
    a11 & a12 & a13\\
    \hline
    a21 & a22 & a23\\
    \hline
    a31 & a32 & a33\\
    \hline
\end{tabular}
\end{document}
```

![Resultado de tabela lado a lado sem legenda no LaTeX]({{ "/assets/LaTeX/Como-colocar-duas-tabelas-lado-a-lado-no-LaTeX-sem-legenda-1.jpg" | relative_url }} "Resultado de tabela lado a lado sem legenda no LaTeX")

Para aplicar legenda às tabelas você pode utilizar o **parbox** para separar as tabelas dentro do ambiente flutuante **table**.

```TeX
\documentclass[12pt]{article}%{standalone}%
\usepackage[papersize={10cm,4cm}, margin=1cm]{geometry}
%\usepackage{graphicx}
\usepackage[export]{adjustbox}

\begin{document}
\centering\begin{table}[!ht]
\parbox{.45\linewidth}{
    \centering
    \begin{tabular}{|c|c|c|}
        \hline
        a11 & a12 & a13\\
        \hline
        a21 & a22 & a23\\
        \hline
        a31 & a32 & a33\\
        \hline
    \end{tabular}
    \caption{Legenda 1}
    \label{tab:tabela1}
}
\hfill
\parbox{.45\linewidth}{
    \begin{tabular}{|c|c|c|}
        \hline
        a11 & a12 & a13\\
        \hline
        a21 & a22 & a23\\
        \hline
        a31 & a32 & a33\\
        \hline
    \end{tabular}
    \caption{Legenda 2}
    \label{tab:tabela2}
}
\end{table}
\end{document}
```

![Resultado de tabela lado a lado no LaTeX]({{ "/assets/LaTeX/tabela-lado-a-lado-com-legenda-1.jpg" | relative_url }} "Resultado de tabela lado a lado no LaTeX")

{%- include end_article.html -%}
