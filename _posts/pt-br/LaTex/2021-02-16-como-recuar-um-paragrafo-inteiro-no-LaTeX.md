---
layout: post
lang: pt-BR
title: "Como recuar um parágrafo inteiro no LaTeX"
date: 2021-02-16 18:00:00 -0400
description: "Neste artigo você descobre como recuar um parágrafo inteiro no LaTeX."
image: "/assets/LaTeX/thumb/thumb-recuo-de-paragrafo-no-LaTeX.png"
category: LaTeX
tags: LaTeX
---

Aprenda três maneiras de recuar um parágrafo inteiro no LaTeX.

<!-- Youtube Video -->
<div class="yt-video">
<iframe width="560" height="315" src="https://www.youtube.com/embed/SS5bQSSqtMI?si=FutyHPoulOpxhZgh" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>

## 1. Recuo de parágrafo com ambiente minipage

Você não precisa de nenhum pacote especial para usar o ambiente `minipage`.

O truque aqui é utilizar o comando `\hfill` antes desse ambiente para empurrar a minipágina para o lado direito. Isso já vai criar um recuo.

Mas o ambiente minipage requer um parâmetro obrigatório, que é o comprimento da mini-página.

Para recuar um parágrafo inteiro no LaTeX neste ambiente, você deve inserir esse parâmetro da seguinte forma:

```TeX
\begin{minipage}{comprimento}
...
\end{minipage}
```

### Veja um exemplo prático

Se você quiser que a mini-página tenha um comprimento de 70% do comprimento total disponível para o texto, os outros 30% vão corresponder ao recuo do parágrafo.

Nesse caso, seu código ficaria assim:

```TeX
\documentclass[12pt]{article}
\usepackage{lipsum}
\begin{document}
\lipsum[1]\hfill

\begin{minipage}{0.7\textwidth}
\lipsum[1]
\end{minipage}

\lipsum[1]
\end{document}
```

![Recuo de parágrafo no LaTeX]({{ "/assets/LaTeX/recuo-de-paragrafo-no-latex.jpg" | relative_url }} "Recuo de parágrafo no LaTeX")

## 2. Recuo de parágrafo com pacote changepage

Outra forma de realizar o recuo de uma página inteira no LaTeX é com o pacote **changepage** que disponibiliza o ambiente **adjustwidth**.

A vantagem deste ambiente, comparando com o minipage, é que se o conteúdo for muito grande então ele pode ser quebrado entre as páginas.

Por isso, este ambiente requer dois parâmetros obrigatórios, que estabelecem o recuo do lado esquerdo e o recuo do lado direito.

Para recuar um parágrafo inteiro no LaTeX neste ambiente, faça o seguinte:

```TeX
\begin{adjustwidth}{recuo esquerda}{recuo direita}
...
\end{adjustwidth}
```

### Veja um exemplo prático

Então se a gente considerar o mesmo contexto do exemplo feito com o ambiente minipage, temos o seguinte código:

```TeX
\documentclass[12pt]{article}
\usepackage{lipsum}
\usepackage{changepage}

\begin{document}
\lipsum[1]

\begin{adjustwidth}{.3\textwidth}{}
\lipsum[1]
\end{adjustwidth}

\lipsum[1]
\end{document}
```

![Recuo de parágrafo no LaTeX]({{ "/assets/LaTeX/recuo-de-paragrafo-no-latex.jpg" | relative_url }} "Recuo de parágrafo no LaTeX")

## 3. Recuo de parágrafo com o comando \leftskip

Você também por criar um recuo a partir de um ponto específico para todo o resto do seu documento usando o comando a seguir.

```TeX
\setlength{\leftskip}{recuo}
```

Em `{recuo}` você vai digitar a largura do recuo desejado.

### Veja um exemplo prático

Então agora vamos considerar que você quer recuar 5 cm do seu texto a partir de um ponto específico dele.

Nesse caso, temos o seguinte código:

```TeX
\documentclass[12pt]{article}
\usepackage{lipsum}

\begin{document}
\lipsum[1]

\setlength{\leftskip}{5cm}
\lipsum[1]

\lipsum[1]
\end{document}
```

![Recuo de parágrafo no LaTeX]({{ "/assets/LaTeX/recuo-de-paragrafo-no-latex-2.jpg" | relative_url }} "Recuo de parágrafo no LaTeX")

{%- include end_article.html -%}
