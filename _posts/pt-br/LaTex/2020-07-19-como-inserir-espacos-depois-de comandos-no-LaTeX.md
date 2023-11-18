---
layout: post
lang: pt-BR
title: "Como inserir espaços depois de comandos no LaTeX"
date: 2020-07-19 18:00:00 -0400
description: "Neste artigo você descobre como inserir espaços depois de comandos no LaTeX."
image: "/assets/LaTeX/thumb/thumb-insercao-de-espacos-depois-de-comandos-no-LaTeX.png"
category: LaTeX
tags: LaTeX
---

Se você ainda não sabe como inserir espaços depois de comandos no LaTeX, já deve ter percebido um problema.

O que acontece é que o LaTeX ignora os espaços digitados e insere o próximo conteúdo logo ao lado.

<!-- Youtube Video -->
<div class="yt-video">
<iframe src="https://www.youtube.com/embed/F2TbHIgUyEo?si=95Uq3KFnSefo0lEz" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>

Para criar esse espaço, você precisa informar ao compilador do LaTeX para parar a varredura do comando.

Você pode realizar essa quebra de varredura inserindo uma `\ (barra invertida)` ou `{}` (chaves) logo depois do comando.

```TeX
O \LaTeX funciona assim. % Sem espaço
O \LaTeX\ funciona assim. % Com espaço
O \LaTeX{} funciona assim. % Com espaço
```

## Quando possuir uma macro definida

Quando você tem uma macro definida, por exemplo:

```TeX
\newcommand{\eea}{Estudantes Em Apuros}
```

Você pode utilizar o pacote `xspace` e o comando `\xspace` para definir o fim da macro e então considerar o espaço.

```TeX
\documentclass[12pt]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage{xspace}
\newcommand{\eea}{Estudantes Em Apuros\xspace}

\begin{document}
O  blog \eea me ajuda pra caramba.
\end{document}
```

E essa é a forma correta de inserir espaços depois de comandos no LaTeX!

{%- include end_article.html -%}
