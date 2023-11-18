---
layout: post
lang: pt-BR
title: "Como adicionar um espaço vertical no início da página no LaTeX"
date: 2020-09-27 18:00:00 -0400
description: "Neste artigo você descobre como adicionar um espaço vertical no início da página no LaTeX."
image: "/assets/LaTeX/thumb/thumb-espaco-vertical-no-inicio-da-pagina-no-LaTeX.png"
category: LaTeX
tags: LaTeX
---

Se estiver utilizando o LaTeX, saiba que existe um jeito muito simples de adicionar um espaço vertical no início de uma página com o comando `\vspace`.

Você provavelmente vai memorizar esse comando com facilidade quando souber que ele é uma abreviação de "vertical space" (espaço vertical em inglês).

Para escolher o tamanho desse espaço vertical, é muito fácil.

Basta você inserir entre chaves, depois do comando, o espaço vertical que quer adicionar ao início da página e antes do texto propriamente dito do seu docmeunto.

Você pode utilizar várias unidades de medida, mas a mais comum é em centímetros. É a medida que a ABNT usa para definir suas margens e é a que vamos usar nos exemplos a seguir.

**Mas cuidado!** Se você adicionar esse comando logo no início da página, ele vai ser **completamente ignorado** pelo LaTeX.

<!-- Youtube Video -->
<div class="yt-video">
<iframe src="https://www.youtube.com/embed/RBKS7G4ffts?si=r0zfflH2Bej9xpES" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>

## Veja um exemplo de **como não fazer**:

```TeX
\documentclass[12pt,a4paper]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage{lipsum}

\begin{document}
  \vspace{7cm}
  \lipsum[1]
\end{document}
```

Perceba que a primeira linha do código do documento (que começa após \begin{document}) é justamente o comando `\vspace`, que adiciona 7 centímetros de espaço vertical no início da página.

Veja o que o LaTeX vai compilar e imprimir nesse caso:

![Espaço vertical no início do documento em LaTeX]({{ "/assets/LaTeX/espaco-vertical-no-inicio-do-documento-latex.jpg" | relative_url }} "Espaço vertical no início do documento em LaTeX")

Perceba que é como se o LaTeX ignorasse o comando. Ou seja, é como se você nunca tivesse colocado o <span class=\"has-inline-color has-vivid-purple-color\">**\vspace**</span> no código.

Para impedir que essa exclusão ocorra basta adicionar o `*` antes da abertura de chaves do comando `\vspace`.

## Veja o exemplo de **como fazer**:

```TeX
\documentclass[12pt,a4paper]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage{lipsum}

\begin{document}
  \vspace*{7cm}
  \lipsum[1]
\end{document}
```

Nesse caso, o LaTeX vai compilar e imprimir o seguinte:

![Espaço vertical no início do documento em LaTeX]({{ "/assets/LaTeX/espaco-vertical-no-comeco-de-uma-pagina-no-latex-1.jpg" | relative_url }} "Espaço vertical no início do documento em LaTeX")

Portanto, quando quiser adicionar um espaço vertical no início da página do seu documento no LaTeX, lembre-se sempre de incluir um \* no comando `\vspace`, ou não vai adiantar de nada inserí-lo no seu código.

{%- include end_article.html -%}
