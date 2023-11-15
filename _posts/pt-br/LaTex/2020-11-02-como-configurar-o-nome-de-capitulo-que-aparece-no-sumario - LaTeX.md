---
layout: post
lang: pt-BR
title: "Como configurar o nome de capítulo que aparece no sumário - LaTeX"
date: 2020-11-02 18:00:00 -0400
description: "Neste artigo você descobre como configurar o nome de capítulo que aparece no sumário do seu documento LaTeX."
image: "/assets/LaTeX/thumb/thumb-latex-2.jpg"
category: LaTeX
tags: LaTeX
---

Em algum momento você está escrevendo um documento e quer que o título que é exibido no sumário seja diferente do título do capítulo.

E mais, você quer que o título que apareça no cabeçalho também seja diferente.

A solução para isso é bem simples

Os comandos de seccionamento / hierarquia possuem um parâmetro opcional que é utilizado para informar o título que desejamos que apareça no sumário.

Esse título deve ser passado entre colchetes antes das chaves.

```TeX
\chapter[título do sumpario]{título no documento}
```

O mesmo padrão serve para seções, subseções e etc.

```TeX
\section[título do sumpario]{título no documento}
\subsection[título do sumpario]{título no documento}
[...]
```

Você ainda pode escolher o nome que aparece no cabeçalho para o capítulo com o comando `\chaptermark`

```TeX
\chaptermark{título para o cabeçalho}
```

<br>

{%- include end_article.html -%}
