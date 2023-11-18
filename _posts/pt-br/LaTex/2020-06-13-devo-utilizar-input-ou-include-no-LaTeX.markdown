---
layout: post
lang: pt-BR
title: 'Devo utilizar \input ou \include no LaTeX?'
date: 2020-06-13 18:00:00 -0400
description: "Neste artigo você descobre qual forma de incluir arquivo você deve utilizar no LaTeX se \\input ou \\include."
image: "/assets/LaTeX/thumb/thumb-input-ou-include-Importacao-de-documento-externo-no-LaTeX.jpg"
category: LaTeX
tags: LaTeX
---

Para organizar documentos, é comum utilizar \\input ou \\include no LaTeX.

Apesar de terem a mesma função, que é importar um arquivo e o incluir no documento .tex de destino, eles tem algumas diferenças.

<!-- Youtube Video -->
<div class="yt-video">
<iframe width="560" height="315" src="https://www.youtube.com/embed/tpYTt6QghaM?si=ZVxXdVPxqfALSE1f" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>

## Comando \\input

O comando `\input{arquivo}` importa todo o conteúdo dentro de arquivo .tex para o arquivo de destino.

Em outras palavras, é como se você digitasse todo o conteúdo de arquivo .tex diretamente no arquivo de destino.

Além disso, o `\input{arquivo}` pode ser utilizado em outros arquivos .tex que não são o arquivo principal a ser compilado.

## Comando \\include

Enquanto o comando `\include{arquivo}` pode ser usado apenas no arquivo que vai compilado, dentro do ambiente <em>document.</em>

Além disso, o comando `\include{arquivo}` limpa a página antes e depois de inserir o documento.

Ele praticamente funciona como um `\input` com os comando `\clearpage` antes e depois:

{% highlight TeX %}
\clearpage
\input{arquivo}
\clearpage
{% endhighlight %}

O comando `\include` também especifica quais arquivos serão incluídos quando utilizado junto ao comando `\includeonly{arquivo1,arquivo2,...}`.

Dessa forma, você pode compilar um projeto muito grande de maneira mais rápida já que você vai incluir apenas dos arquivos especificados.

Essa é a diferença de utilizar \\input ou \\include no LaTeX.

{%- include end_article.html -%}
