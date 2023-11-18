---
layout: post
lang: pt-BR
title: 'Por que o \label tem que vir depois do \caption?'
date: 2020-11-18 18:00:00 -0400
description: "Neste artigo você descobre por que o \\label tem que vir depois do \\caption."
image: "/assets/LaTeX/thumb/thumb-por-que-o-label-deve-vir-depois-de-caption-LaTeX.png"
category: LaTeX
tags: LaTeX
channel-id: UCYUU9jqWR41rkRXBQHBdbtw
---

No LaTeX, a ordem dos fatores altera sim o produto. Para que você **não se depare com erros na legenda da sua imagem**, eu vou responder a dúvida de um Estudante: por que o `\label` tem que vir sempre depois do `\caption`?

A resposta para isso é bem simples. Veja como o LaTeX interpreta cada um desses comandos:

<!-- Youtube Video -->
<div class="yt-video">
<iframe src="https://www.youtube.com/embed/ZPfOo5l0v2k?si=mF3TgksVBGhaat4J" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>

{%- include subscribe-channel.html -%}


O comando `\caption` é responsável por **gerar a numeração**. Imagine isso como a geração de um \"endereço\". Por exemplo, uma figura.

E o comando `\label` é utilizado para **marcar o caption que será referenciado** em outras partes do seu texto.

Em outras palavras, ele guarda a informação do \"endereço\" de uma legenda gerada pelo comando `\caption`, por exemplo, o endereço de uma figura dentro do seu documento.

Assim como não podemos falar de um endereço que não existe, o `\label` não tem como se referir a uma legenda que não foi numerado pelo `\caption`.

## Veja um exemplo prático de inserção do \label depois do \caption em uma figura:

Vamos supor que você quer inserir uma imagem no seu documento e sabe que, mais à frente, vai querer falar dessa imagem.

Você primeiro vai **criar a legenda** dessa imagem com o comando `\caption` - que significa legenda em inglês.

Nessa legenda, você deve escrever uma breve descrição do que a imagem representa para o seu texto. No exemplo a seguir, vamos usar a legenda \"Exemplo de figura\".

Uma vez que você inseriu a figura e sua respectiva legenda, é hora de **criar um marcador para essa legenda**. Assim você vai poder citá-la mais facilmente ao longo do texto.

É hora então de usar o `\label` - que significa etiqueta ou marcador em inglês, mas você pode interpretar como \"apelido\" aqui no LaTeX.

Consideramos uma boa prática inserir prefixos no `\label` indicando qual é o tipo de informação que você está marcando.

Por exemplo, se for uma figura insira **fig:** antes do nome escolhido. Se for uma tabela, insira **tab:**. E assim por diante.

Seguindo essa lógica, vamos inserir o marcador (ou apelido) \"fig:figura\" no nosso exemplo:

```TeX
\begin{figure}
    \centering
    \includegraphics[width=.5\linewidth]{example-image-a}
    \caption{Exemplo de figura}
    \label{fig:figura}
\end{figure}
```

Da mesma forma, você deve criar a marcação para capítulos, seções e demais comandos que geram numeração.

E o comando `\label` deve sempre ser colocado depois.

## Exemplo prático de inserção do \label depois do \caption em uma figura:

Por exemplo, para referenciar uma seção, o código seria:

```TeX
\documentclass[12pt]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage{lipsum}

\begin{document}
\section{Seção}
\lipsum[1][1-10]
Veja a figura \ref{fig:figura} na seção \ref{sec:secaoFig}.

\section{Outra seção} \label{sec:secaoFig}
\begin{figure}
    \centering
    \includegraphics[width=.5\linewidth]{example-image-a}
    \caption{Exemplo de figura}
    \label{fig:figura}
\end{figure}

\lipsum[1][1-10]
\end{document}
```

<br>

{%- include end_article.html -%}
