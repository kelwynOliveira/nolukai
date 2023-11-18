---
layout: post
lang: pt-BR
title: "Como alterar a orientação de páginas no LaTeX para paisagem (horizontal)"
date: 2020-08-10 18:00:00 -0400
description: "Neste artigo você descobre como alterar a orientação de páginas no LaTeX para paisagem (horizontal)"
image: "/assets/LaTeX/thumb/thumb-como-alterar-a-orientacao-de-algumas-paginas-no-LaTeX-para-paisagem-(horizontal).png"
category: LaTeX
tags: LaTeX
channel-id: UCYUU9jqWR41rkRXBQHBdbtw
---

Se você quer saber como alterar a orientação das páginas para o modo de paisagem (horizontal) no LaTeX, você está no lugar certo!

Neste artigo, vamos te mostrar duas maneiras diferentes - utilizando pacotes diferentes - para que você faça essa alteração com sucesso.

<!-- Youtube Video -->
<div class="yt-video">
<iframe src="https://www.youtube.com/embed/PY18DEa77Fo?si=TMv_c7L45WUajpHq" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>

{%- include subscribe-channel.html -%}


## Utilizando o pacote **lscape**

Vamos usar um exemplo para ilustrar esse comando mas, caso você queira saber mais detalhes, pode <a href="https://www.ctan.org/pkg/lscape" target="_blank">consultar toda a documentação deste pacote</a>.

Entre os ambientes disponíveis neste pacote, está o ambiente `landscape` (paisagem, em inglês), que é compatível com os pacotes `longtable` e `supertabular`.

Dentro do ambiente `landscape`, você pode alterar as margens da folha e rotacionar o conteúdo para que ele fique na horizontal.

Mas fique tranquilo porque isso não vai alterar direção do PDF compilado!

Veja como utiliza

```TeX
\documentclass[12pt]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage{lipsum}
\usepackage{lscape}

\begin{document}
\section{Aqui é uma seção}
\lipsum

\begin{landscape}
\lipsum[1]
\end{landscape}

\end{document}
```

Caso você ainda não esteja satisfeito com o resultado gerado pelo pacote `lscape`, você pode recorrer a outro pacote.

## Utilizando o pacote **pdfscape**

Assim como no pacote lscape, você pode utilizar o ambiente `landscape` dentro pacote `pdfscape`.

A diferença é que no pacote `pdfscape`, a folha (PDF) será alterada para o modo de paisagem (horizontal) no LaTeX.

Então veja um exemplo de como utilizar o pacote `pdflscape`.

```TeX
\documentclass[12pt]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage{lipsum}
\usepackage{pdflscape}

\begin{document}
\section{Aqui é uma seção}
\lipsum

\begin{landscape}
\lipsum[1]
\end{landscape}

\end{document}
```

Caso ainda tenha alguma dúvida em relação a esse pacote, você pode a sua documentação clicando <a href="https://www.ctan.org/pkg/pdflscape" target="_blank">aqui</a>.

{%- include end_article.html -%}
