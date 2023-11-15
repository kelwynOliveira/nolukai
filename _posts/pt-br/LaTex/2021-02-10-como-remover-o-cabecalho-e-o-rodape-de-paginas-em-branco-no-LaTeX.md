---
layout: post
lang: pt-BR
title: "Como remover o cabeçalho e o rodapé de páginas em branco no LaTeX"
date: 2021-02-10 18:00:00 -0400
description: "Neste artigo você descobre como remover o cabeçalho e o rodapé de páginas em branco no LaTeX."
image: "/assets/LaTeX/thumb/thumb-latex-5.jpg"
category: LaTeX
tags: LaTeX
---

Se está procurando como remover o cabeçalho e o rodapé de páginas em branco no LaTeX, você encontrou o artigo certo!

Antes de partir para os comandos...

## Vamos lembrar a configuração básica de cabeçalhos e rodapés em páginas em branco no LaTeX

- Quando você cria um projeto, por exemplo, com a classe **book**, o LaTeX cria um documento com impressão ativa para os dois lados de uma folha;
- E quando você insere um capítulo, esse capítulo só será impresso em páginas ímpares (leitura na direita).

**E por que isso importa?**

Você precisa saber disso porque se antes de adicionar um capítulo seu texto acabar em uma página ímpar, o LaTeX vai imprimir a página par seguinte em branco para que o início do capítulo apareça em uma página ímpar.

Mas é claro que essa é apenas a configuração padrão e pode ser reconfigurada.

## E quando você quiser que o documento tenha essa configuração?

Mesmo que você queira deixar os inícios de capítulo sempre em página ímpar, uma página em branco mas com conteúdo no cabeçalho e no rodapé nem sempre são desejáveis.

Então veja como a impressão do LaTeX para uma página sem rodapé definido:

![Remoção do cabeçalho e do rodapé em páginas em branco no LaTeX]({{ "/assets/LaTeX/remocao-do-cabecalho-e-do-rodape-em-paginas-em-branco-no-latex.jpg" | relative_url }} "Remoção do cabeçalho e do rodapé em páginas em branco no LaTeX")

Para remover o conteúdo do cabeçalho e do rodapé e realmente ficar com páginas em branco no LaTeX, você pode recorrer ao pacote `emptypage`. Como no exemplo:

```TeX
\documentclass[12pt,a4paper]{book}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage{emptypage}
\usepackage{lipsum}

\begin{document}
\chapter{O início}
\lipsum[1]\

chapter{O final}
\lipsum

\end{document}
```

Assim os cabeçalhos e rodapés serão removidos das páginas em branco automaticamente.

{%- include end_article.html -%}
