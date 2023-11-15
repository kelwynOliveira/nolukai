---
layout: post
lang: pt-BR
title: 'Qual a diferença entre \textwidth, \linewidth e \hsize'
date: 2020-09-03 18:00:00 -0400
description: "Neste artigo você descobre qual a diferença entre \\textwidth, \\linewidth e \\hsize."
image: "/assets/LaTeX/thumb/thumb-latex-6.jpg"
category: LaTeX
tags: LaTeX
---

Vamos distinguir a diferença entre os comandos de largura utilizados no LaTeX, dentre eles o `\textwidth`, `\linewidth`, `\hsize` e `\columnwidth`.

Começarei por `\hsize`, esse é um parâmetro do TeX que normalmente não deve ser utilizado em LaTeX. Sempre que um parágrafo é finalizado é feito uma verificação do valor desse parâmetro para então quebrá-lo em caixas horizontais.

O parâmetro `\textwidth` é a largura global da área de texto do seu documento. O conteúdo pode ter uma ou mais colunas, mas o valor de `\texwidth` não altera.

Quando o `\textwidth` é utilizado dentro de um ambiente `minipage` ele recebe o valor interno da minipage. Quando finalizado o ambiente `\textwidth` volta para o seu valor \"padrão\".

Se o documento for de uma coluna o valor de `\columnwidth` é o mesmo de `\textwidth`, já quando o documento tem mais de uma coluna o valor de `\columnwidth` é diferente de `\textwidth`. Ou seja, o `\columnwidth` é a largura de uma coluna de texto.

Por último o parâmetro `\linewidth`, ele representa a largura da linha texto atual, ou seja, é um valor que pode variar de acordo com o local que ele é utilizado, dentro de uma minipage, coluna, lista...

Você pode utilizar esses parâmetros como unidades de comprimento. Por exemplo uma figura com metade da largura da linha atual pode ser definida como `width=0.5\linewidth`, ou 90% da área de texto como `width=.9\textwidth`.

{%- include end_article.html -%}
