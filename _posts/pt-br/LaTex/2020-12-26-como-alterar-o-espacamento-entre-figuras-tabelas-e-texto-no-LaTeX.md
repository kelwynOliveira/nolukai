---
layout: post
lang: pt-BR
title: "Como alterar o espaçamento entre figuras/tabelas e texto no LaTeX"
date: 2020-12-26 18:00:00 -0400
description: "Neste artigo você descobre como alterar o espaçamento entre figuras/tabelas e texto no LaTeX."
image: "/assets/LaTeX/thumb/thumb-latex-4.jpg"
category: LaTeX
tags: LaTeX
---

As figuras e tabelas criadas no LaTeX são normalmente inseridas utilizando ambientes flutuantes.

Chamamos de ambientes flutuantes aqueles que podem ser inseridos em qualquer posição que o codificador achar mais adequado.

Por exemplo, uma figura inserida dentro do ambiente **figure** pode ficar no topo da página [t], na parte de baixo da página [b], em uma página só de ambientes flutuantes [p] ou na posição em que o código foi inserido [h].

No código abaixo é dito para a figura priorizar a posição atual, caso a posição não seja boa seguirá para o topo, ou parte de baixo ou uma página de ambiente flutuante.

```TeX
\documentclass[12pt]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage{graphicx}
\usepackage{lipsum}

\begin{document}
\lipsum[1]

\begin{figure}[!htbp]
    \centering
    \includegraphics[width=\linewidth]{imagem1.jpg}
    \caption{Imagem}
    \label{fig:imagem1}
\end{figure}

\lipsum[1]
\end{document}
```

Levando em consideração o posicionamento do ambiente flutuante podemos configurar a distância entre ele e o texto do nosso documento.

## Configuração da distância dos ambientes flutuantes

Existem três macros que nos permitem configurar as distâncias (em conjunto do comando \setlength):

- `\textfloatsep` - distância entre o ambiente flutuante no topo e o texto, ou ambiente na parte de baixo e o texto.
- `\floatsep` - distância entre dois ambientes flutuantes.
- `\intextsep` - distância entre ambientes flutuantes utilizando o posicionamento [h] e o texto.

Para saber qual é a configuração de posicionamento que o documento está utilizando você pos utilizar o comando `\showthe\textfloatsep` ou `\the\textfloatsep` (para o floatsep).

Caso queira saber a distância das outras macros basta trocar o \textfloatsep pela macro desejada.

Considere o mesmo código utilizado acima, agora com configuração para que a imagem tenha uma distância de 40pt pra cima e para baixo quando ela estiver entre textos [h].

```TeX
\documentclass[12pt]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage{graphicx}
\usepackage{lipsum}
\setlength{\intextsep}{40pt plus 1.0pt minus 2.0pt}

\begin{document}
\lipsum[1]

\begin{figure}[!htbp]
    \centering
    \includegraphics[width=\linewidth]{imagem1.jpg}
    \caption{Imagem}
    \label{fig:imagem1}
\end{figure}

\lipsum[1]
\end{document}
```

O **plus** e **minus** se referem ao quanto o espaço deve esticar ou encolher quando isso for necessário. Quanto maiores mais o espaçamento se encolhe ou estica.

Se você estiver escrevendo no modo de duas colunas você também pode utilizar as macros:

- `\dbltextfloatsep` - distância entre um ambiente flutuante abrangendo as duas colunas e o texto.
- `\dblfloatsep` - distância entre dois ambientes flutuantes abrangendo as duas colunas.

{%- include end_article.html -%}
