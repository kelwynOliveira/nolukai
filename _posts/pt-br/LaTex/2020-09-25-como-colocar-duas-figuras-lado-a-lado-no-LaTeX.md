---
layout: post
lang: pt-BR
title: "Como colocar duas figuras lado a lado no LaTeX"
date: 2020-09-25 18:00:00 -0400
description: "Neste artigo você descobre como colocar duas figuras lado a lado no LaTeX."
image: "/assets/LaTeX/thumb/thumb-latex-2.jpg"
category: LaTeX
tags: LaTeX
---

Aqui vamos descobrir como colocar duas, ou mais, figuras lado a lado no LaTeX. Existem várias formas, apresentarei duas.

## Com ambiente minipage

Colocar uma figura lado a lado no LaTeX é mais simples do que você imagina. Você pode utilizar o ambiente minipage para fazer isso.

Dentro do ambiente flutuante **figure** você insere um ambiente **minipage** para cada uma das imagens:

```TeX
\begin{figure}[!ht]
    \centering
    \begin{minipage}{0.5\textwidth}
        \centering
        \includegraphics[width=0.9\textwidth]{example-image-a}
        \caption{Figura 1}
        \label{fig:figura1minipg}
    \end{minipage}\hfill
    \begin{minipage}{0.5\textwidth}
        \centering
        \includegraphics[width=0.9\textwidth]{example-image-b}
        \caption{Figura 2}
        \label{fig:figura2minipg}
    \end{minipage}
    \caption{Exemplo de figuras}
    \label{fig:figurasminipg}
\end{figure}
```

O comando **\hfill** no final do primeiro ambiente **figure** coloca um ambiente ao lado do outro. Para entende o funcionamento dos parâmetros **\textwidth e \linewidth** leia este artigo: [Qual a diferença entre \textwidth, \linewidth e \hsize]({{ "/qual-a-diferenca-entre-textwidth-linewidth-e-hsize" | relative_url }})

## Com ambiente subfigure

Para utilizar o ambiente **subfigure** você vai precisar do pacote **subcaption**.

```TeX
\documentclass[12pt,a4paper]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage{graphicx}
\usepackage{subcaption}

\begin{document}
\begin{figure}[!ht]
    \begin{subfigure}{.5\textwidth}
        \centering
        \includegraphics[width=0.9\linewidth]{example-image-a}
        \caption{Figura 1}
        \label{fig:figura1subfig}
    \end{subfigure}
    \begin{subfigure}{.5\textwidth}
        \centering
        \includegraphics[width=0.9\linewidth]{example-image-b}
        \caption{Figura 2}
        \label{fig:figura2subfig}
    \end{subfigure}

    \caption{Exemplo de figuras}
    \label{fig:figuras}

\end{figure}
\end{document}
```

## Resultado

A diferença entre os dois métodos está basicamente na forma que as legendas são apresentadas.

Com o ambiente **subfigure** a numeração da figura é feita com letras minúsculas.

![Resultado de imagem lado a lado]({{ "/assets/LaTeX/image.png" | relative_url }} "Resultado de imagem lado a lado")

{%- include end_article.html -%}
