---
layout: post
lang: pt-BR
title: "Como numerar a linha de tabelas de forma automática no LaTeX"
date: 2021-05-17 18:00:00 -0400
description: "Neste artigo você descobre como numerar a linha de tabelas de forma automática no LaTeX."
image: "/assets/LaTeX/thumb/thumb-latex-2.jpg"
category: LaTeX
tags: LaTeX
---

Neste artigo você vai descobrir como numerar a linha de tabelas de forma automática no LaTeX.

Para criar essa tabela é preciso dois pacotes: **array** (<a href="https://www.ctan.org/pkg/array" target="_blank">documentação</a>) para criarmos o novo tipo de coluna e **etoolbox** (<a href="https://www.ctan.org/pkg/etoolbox" target="_blank">documentação</a>) para fazermos a programação da contagem.

```TeX
\documentclass[12pt]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage{array}
\usepackage{etoolbox}%Contagem da linha
\preto\tabular{\setcounter{numerolinha}{0}}

\newcounter{numerolinha}

\newcommand\rownumber{\stepcounter{numerolinha}\arabic{numerolinha}}%novo tipo de coluna

\newcolumntype{K}{@{\makebox[3em][c]{\rownumber\space}}}\begin{document}\begin{tabular}{| K | l |}
    \hline
    Conteúdo da linha 1 \\
    \hline
    Conteúdo da linha 2 \\
    \hline
    Conteúdo da linha 3\\
    \hline
\end{tabular}\end{document}
```

Caso você não queira que a contagem comece a partir da primeira linha use o código abaixo:

```TeX
\documentclass[12pt]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage{array}
\usepackage{etoolbox}%Contagem da linha
\preto\tabular{\setcounter{numerolinha}{0}}

\newcounter{numerolinha}
\def\rownumber{}%novo tipo de coluna

\newcolumntype{K}{@{\makebox[3em][c]{\rownumber\space}}}\begin{document}\begin{tabular}{| K | l |}
    \hline
    Conteúdo da linha 1
    \gdef\rownumber{\stepcounter{numerolinha}\arabic{numerolinha}}\\
    \hline
    Conteúdo da linha 2 \\
    \hline
    Conteúdo da linha 3\\
    \hline
\end{tabular}\end{document}
```

O comando **\gdef\rownumber{\stepcounter{numerolinha}\arabic{numerolinha}}** deve ser inserido antes da quebra de linha da qual se deseja iniciar a contagem.

No código acima foi inserido na linha 1 da tabela para que a contagem se inicie a partir da segunda linha da tabela.

![Como numerar a linha de tabelas de forma automática no LaTeX]({{ "/assets/LaTeX/Como-numerar-a-linha-de-tabelas-de-forma-automatica-no-LaTeX.jpg" | relative_url }} "Como numerar a linha de tabelas de forma automática no LaTeX")

Caso você queira colocar um conteúdo na primeira célula utilize o comando **\multicolumn**, veja o código abaixo:

```TeX
\documentclass[12pt]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage{array}
\usepackage{etoolbox}%Contagem da linha
\preto\tabular{\setcounter{numerolinha}{0}}

\newcounter{numerolinha}
\def\rownumber{}

%novo tipo de coluna

\newcolumntype{K}{@{\makebox[3em][c]{\rownumber\space}}}\begin{document}\begin{tabular}{| K | l |}
    \hline
    \multicolumn{1}{|@{\makebox[3em][c]{cel1~}} | l |}{Conteúdo da linha 1}
    \gdef\rownumber{\stepcounter{numerolinha}\arabic{numerolinha}}\\
    \hline
    Conteúdo da linha 2 \\
    \hline
    Conteúdo da linha 3\\
    \hline
\end{tabular}\end{document}
```

![Como numerar a linha de tabelas automaticamente]({{ "/assets/LaTeX/como-numerar-a-linha-de-tabelas-automaticamente.jpg" | relative_url }} "Como numerar a linha de tabelas automaticamente")

{%- include end_article.html -%}
