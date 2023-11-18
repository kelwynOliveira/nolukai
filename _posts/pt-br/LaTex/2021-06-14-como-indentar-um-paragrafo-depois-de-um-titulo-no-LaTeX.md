---
layout: post
lang: pt-BR
title: "Como indentar um parágrafo depois de um título no LaTeX"
date: 2021-06-14 18:00:00 -0400
description: "Neste artigo você descobre como indentar um parágrafo depois de um título no LaTeX."
image: "/assets/LaTeX/thumb/thumb-indentacao-do-paragrafo-depois-de-um-titulo-no-LaTeX.png"
category: LaTeX
tags: LaTeX
channel-id: UCYUU9jqWR41rkRXBQHBdbtw
---

De acordo com o padrão do LaTeX (EUA), o primeiro parágrafo depois de um título não sofre indentação. Mas e em textos em português? Como indentar um parágrafo depois de um título no LaTeX?

<!-- Youtube Video -->
<div class="yt-video">
<iframe src="https://www.youtube.com/embed/uQrUz_3zyWc?si=F5V2MMOgaXSBgz7p" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>

{%- include subscribe-channel.html -%}


Você vai precisar verificar se está usando alguns pacotes no seu documento:

- inputenc;
- fontenc;
- babel;
- lipsum.

Com esses pacotes inseridos, você vai definir o tamanho da indentação com o comando `\setlength{\parindent}{}`.

Dentro do segundo par de chaves, você vai digitar o tamanho desejado.

Por exemplo, se você quiser definir uma indentação de 2 cm, utilize o seguinte código:

```TeX
\documentclass[12pt]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage{lipsum}
\setlength{\parindent}{2cm}

\begin{document}
  \section{Seção}
  \lipsum[1-2]
\end{document}
```

![Indentação do primeiro parágrafo no LaTeX]({{ "/assets/LaTeX/indentacao-do-primeiro-paragrafo-no-LaTeX.jpg" | relative_url }} "Indentação do primeiro parágrafo no LaTeX")

Mas como você deve ter visto, o comando `\setlength{\parindent}{tamanho}` só define o tamanho da indentação.

Ele segue o padrão dos EUA, então não faz com que o primeiro parágrafo seja indentado.

Para fazer com que o primeiro parágrafo de todas as seções sofra obrigatoriamente o recuo, insira no preâmbulo do seu documento LaTeX o pacote **indentfirst**:

```TeX
\documentclass[12pt]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage{lipsum}
\usepackage{indentfirst}
\setlength{\parindent}{2cm}

\begin{document}
  \section{Seção}
  \lipsum[1-2]
\end{document}
```

![Indentação do primeiro parágrafo no LaTeX]({{ "/assets/LaTeX/indentacao-do-primeiro-paragrafo-LaTeX-1.jpg" | relative_url }} "Indentação do primeiro parágrafo no LaTeX")

E assim é como indentar um parágrafo depois de um título no LaTeX!

{%- include end_article.html -%}
