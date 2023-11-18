---
layout: post
lang: pt-BR
title: "Como fazer comentários no LaTeX"
date: 2021-05-23 18:00:00 -0400
description: "Neste artigo você descobre como fazer comentários no LaTeX."
image: "/assets/LaTeX/thumb/thumb-comentarios-no-LaTeX.png"
category: LaTeX
tags: LaTeX
---

Os comentários servem para que você entenda o que fez no código mesmo que passe muito tempo longe dele e são uma prática excelente! Mas então como fazer comentários no LaTeX?

<!-- Youtube Video -->
<div class="yt-video">
<iframe width="560" height="315" src="https://www.youtube.com/embed/x43MWDXQ-zQ?si=DT2cRPU3lGVWse5N" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>

## Como fazer um comentário no LaTeX

Quando fazemos um comentário, o compilador do LaTeX ignora esse trecho do código. Ou seja, o que escrevemos nesse trecho não aparece no PDF final do documento.

Para fazer um comentário no LaTeX utilizamos o carctere `%`.

Em uma linha de código, o sinal `%` faz com que o LaTeX ignore tudo o que estiver à direita desse símbolo.

Você pode, inclusive, utilizar esse artifício para fazer desabilitar temporariamente um comando.

Ou seja, pode impedir que uma parte do código seja compilada. Ela não vai aparecer no PDF do documento, mas o código continua ali pronto pra ser usado - basta retirar o `%`.

Mas agora você pode estar se perguntando: se o `%` indica pro LaTeX que eu estou fazendo um comentário, então como eu faço quando quiser escrever uma porcentagem?

É simples: basta usar o comando `\%`.

### Veja um exemplo prático

Imagine que você quer desabilitar o pacote babel do seu código. Basta fazer o seguinte:

```TeX
\documentclass[a4paper, 12pt]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
%\usepackage[brazil]{babel}

\begin{document}
  Texto de exemplo. % este é um comentário de exemploImpressão do símbolo \%.
\end{document}
```

## Comentários de múltiplas linhas no LaTeX

Como dito antes, o LaTeX entende como comentário tudo o que está à direita do `%`.

Isso significa que se você quebrar a linha, o que escrever nessa nova linha não é mais um comentário e aparece no PDF compilado.

Para fazer um comentário de múltiplas linhas no LaTeX, você pode inserir o símbolo de % para cada uma das linhas:

```TeX
\documentclass[a4paper, 12pt]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}

\begin{document}
  Texto de exemplo. % este é um comentário de exemplo% Este é um
  % comentário de
  % múltiplas
  % linhas
\end{document}
```

Mas isso não é praticável em um comentário realmente grande de várias linhas.

Então o ideal, nesse caso, é utilizar o ambiente `comment` disponíveis para o uso com os pacotes `verbatim` ou `comment`:

```TeX
\documentclass[a4paper, 12pt]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage{verbatim}

\begin{document}
Texto de exemplo. % este é um comentário de exemplo

\begin{comment}
    Este é um
    comentário de
    múltiplas
    linhas
\end{comment}
\end{document}
```

E essa é a forma correta de inserir capítulos e seções não numeradas no LaTeX!

{%- include end_article.html -%}
