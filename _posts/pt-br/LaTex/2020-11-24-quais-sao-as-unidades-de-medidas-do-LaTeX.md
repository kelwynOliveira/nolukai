---
layout: post
lang: pt-BR
title: "Quais são as unidades de medidas do LaTeX"
date: 2020-11-24 18:00:00 -0400
description: "Neste artigo você descobre quais são as unidades de medidas do LaTeX."
image: "/assets/LaTeX/thumb/thumb-latex-1.jpg"
category: LaTeX
tags: LaTeX
---

São várias as unidades de medidas que podemos utilizar no LaTeX. As mais utilizadas são:

| Abreviação | Valor                                                   |
| ---------- | ------------------------------------------------------- |
| pt         | ponto, é definido como 1/72,27 polegadas, ou 0,3515 mm  |
| mm         | milímetros                                              |
| cm         | centímetros                                             |
| in         | polegadas                                               |
| ex         | altura do caractere 'x' (minúsculo) na fonte utilizada  |
| em         | largura do caractere 'M' (maiúsculo) na fonte utilizada |

Por exemplo, para definir uma figura com largura de 15 cm podemos escrever:

```TeX
\includegraphics[width=15cm]{imagem1.jpg}
```

Você ainda pode utilizar comandos que armazenam comprimentos para servirem de unidades como:

| Comando       | Descrição                             |
| ------------- | ------------------------------------- |
| `\extheight`  | altura da área de texto na página     |
| `\textwidth`  | largura da área de texto na página    |
| `\linewidth`  | largura da linha no ambiente atual    |
| `\paperwidth` | largura do papel                      |
| `\parindent`  | largura de indentação do parágrafo    |
| `\parskip`    | espaçamento vertical entre parágrafos |

Por exemplo, para definir uma figura com metade da largura da linha podemos escrever:

```TeX
\includegraphics[width=0.5\linewidth]{imagem1.jpg}
```

<br>

{%- include end_article.html -%}
