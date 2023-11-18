---
layout: post
lang: pt-BR
title: "Como forçar o posicionamento de figuras no texto LaTeX"
date: 2020-06-27 18:00:00 -0400
description: "Neste artigo você descobre como forçar o posicionamento de figuras no texto LaTeX."
image: "/assets/LaTeX/thumb/thumb-como-posicionar-figuras-no-LaTeX.png"
category: LaTeX
tags: LaTeX
---

<!-- Youtube Video -->
<div class="yt-video">
<iframe src="https://www.youtube.com/embed/Sx-GIargq6o?si=09auFYgauzoOBuYx" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>

Antes de te mostrar como, é legal que você saiba que é comum que o LaTeX insira uma figura, no PDF final, em um lugar diferente do que você imaginou quando escreveu o código.

Isso acontece principalmente quando você utiliza ambientes flutuantes para posicionar a sua imagem, como é o caso do ambiente `figure` - o mais usado para a inserção de figuras.

Nesse caso, o LaTeX tende a otimizar a posição da figura pra que o documento fique mais bonito e agradável ao leitor.

Outro ponto curioso é que essa decisão também é muito comum em livros.

O que mostra que o LaTeX realmente se preocupa com o leitor.

## Como alterar o posicionamento de figuras feito pelo LaTeX

Só mais um aviso antes de partir para a explicação: nós do Estudantes em Apuros recomendamos que você evite frases como \"na imagem abaixo\".

Prefira usar frases como \"na imagem 1\", usando os comandos de referências cruzadas do LaTeX - pra que ele defina sozinho a numeração da figura.

Pra fazer isso, use o código:

```TeX
\documentclass[12pt, a4paper]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage{graphicx}
\usepackage{lipsum}

\begin{document}

\lipsum

Veja a figura~\ref{fig:imagem}

\begin{figure}
  \centering
  \includegraphics[width=.5\linewidth]{imagem1.jpg}
  \caption{imagem}
  \label{fig:imagem}
\end{figure}

\end{document}
```

## Sobre posicionamento de ambientes flutuantes

O ambiente **figure** ainda recebe parâmetros opcionais em **[posição]**:

```TeX
\begin{figure}[posição]
...
\end{figure}
```

Os argumentos que você vai inserir entre os colchetes indicam onde a figura deve ser posicionada no PDF:

- **[!]**- priorização para colocar na melhor posição
- **[h]**- colocar a figura neste local do código (here - em inglês)
- **[t]** - colocar a figura no topo da página (top - em inglês)
- **[b]** - inserir a figura na parte de baixo da página (bottom - em inglês)
- **[p]** - inserir a figura em uma página de elementos flutuantes (page - em inglês)

Se não informar nenhum parâmetro, o LaTeX vai usar o **[t]** por padrão.

```TeX
\begin{figure}[!ht]
...
\end{figure}
```

Mas saiba que mesmo assim a imagem será colocada na posição que o LaTeX achar mais conveniente.

Se por alguma razão você deseja forçar o posicionamento da imagem em um local específico, utilizando ambientes flutuantes, você pode usar o pacote **float** e informar o posicionamento **H**:

```TeX
\documentclass[12pt, a4paper]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage{graphicx}
\usepackage{float}
\usepackage{lipsum}

\begin{document}
\lipsum

Veja a figura~\ref{fig:imagem}

\begin{figure}[H]
    \centering
    \includegraphics[width=.5\linewidth]{imagem1.jpg}
    \caption{imagem}
    \label{fig:imagem}
\end{figure}
\end{document}
```

E se você for inserir uma imagem que não faz uso de título (**\caption**), nem referência (**\label** \| **\ref**), então nem é necessário o uso do ambiente **figure**.

Nesse caso, você pode inserir diretamente o comando `\includegraphics` no código:

```TeX
\documentclass[12pt, a4paper]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage{graphicx}
\usepackage{lipsum}

\begin{document}
\lipsum
\begin{center}
    \includegraphics[width=.5\linewidth]{imagem1.jpg}
\end{center}
\end{document}
```

Agora você já sabe como posicionar as figuras do seu texto no LaTeX!

{%- include end_article.html -%}
