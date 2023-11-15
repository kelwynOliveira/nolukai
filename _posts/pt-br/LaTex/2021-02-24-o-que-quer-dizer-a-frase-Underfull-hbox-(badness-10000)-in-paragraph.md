---
layout: post
lang: pt-BR
title: 'O que quer dizer a frase "Underfull \hbox (badness 10000) in paragraph" "Underfull \hbox (badness 10000) in paragraph"?'
date: 2021-02-24 18:00:00 -0400
description: 'Neste artigo você descobre o que quer dizer a frase "Underfull \hbox (badness 10000) in paragraph" "Underfull \hbox (badness 10000) in paragraph".'
image: "/assets/LaTeX/thumb/thumb-latex-5.jpg"
category: LaTeX
tags: LaTeX
---

A frase ` Underfull \hbox (badness 10000) in paragraph`` normalmente quer dizer que você possui um comando  `\` posicionado incorretamente no parágrafo.

Isso significa que o conteúdo não foi suficiente para completar o tamanho da caixa separado para o conteúdo.

Ao colocar um `\` no fim do parágrafo, você força uma **quebra de linha** (não parágrafo) em um ponto específico.

```TeX
\begin{document}
Texto de exemplo. \\Continuação do texto.
\end{document}
```

Mas se você notar não tem nada escrito na linha depois de `\`, o que é muito ruim.

E se o conteúdo não for suficiente para completar a linha, o LaTeX vai considerar apenas que a caixa é larga demais.

O oposto desse aviso é o **Overfull \hbox**, ou seja, o conteúdo é tão grande que ultrapassou a largura da caixa.

{%- include end_article.html -%}
