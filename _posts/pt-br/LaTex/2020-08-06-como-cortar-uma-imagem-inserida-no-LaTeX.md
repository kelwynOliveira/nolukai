---
layout: post
lang: pt-BR
title: "Como cortar uma imagem inserida no LaTeX"
date: 2020-08-06 18:00:00 -0400
description: "Neste artigo você descobre como cortar uma imagem inserida no LaTeX."
image: "/assets/LaTeX/thumb/thumb-latex-3.jpg"
category: LaTeX
tags: LaTeX
---

Realizar o corte de uma imagem inserida no LaTeX é bem simples.

Entre os parâmetros opcionais do comando **\includegraphics** podemos passar **trim** e **crop**.

O comando **trim** exige quatro valores para o corte: **trim={esquerda abaixo direita acima}**, ou seja, os valores são informados em sentido anti-horário começando do lado esquerdo da imagem.

Se nenhuma unidade for informada a unidade utilizada será a bp (big points). Adicionar o parâmetro **crop** informa que o corte deve ser realizado.

```TeX
\documentclass[12pt]{article}
\usepackage{graphicx}

\begin{document}
  \includegraphics[trim={1cm 20pt 1cm 30mm},clip]{example-image-a}
\end{document}
```

![corte de imagem no latex]({{ "/assets/LaTeX/corte-de-imagem-com-o-latex.jpg" | relative_url }} "corte de imagem no latex")

Ao combinar esses parâmetros com **width** / ** height** será realizado o corte e então a imagem é redimensionada.

```TeX
\documentclass[12pt]{article}
\usepackage{graphicx}

\begin{document}
  \includegraphics[trim={1cm 0 0 0},clip, width=6cm]{example-image-a}
\end{document}
```

![corte de imagem no latex com redimensão]({{ "/assets/LaTeX/corte-de-imagem-no-latex-com-redimensao.jpg" | relative_url }} "corte de imagem no latex com redimensão")

Caso você queira realizar cortes em relação a proporção da imagem, por exemplo 50% da largura você vai precisar do pacote **adjustbox** para então ter acesso ao width e height.

```TeX
\documentclass[12pt]{article}
\usepackage[export]{adjustbox}

\begin{document}
  \adjincludegraphics[trim={0 0 {.5\width} 0},clip,width=3cm]{example-image-a}
\end{document}
```

![corte de imagem no latex com parametro de largura]({{ "/assets/LaTeX/corte-de-imagem-no-latex-com-parametro-de-largura.jpg" | relative_url }} "corte de imagem no latex com parametro de largura")

{%- include end_article.html -%}
