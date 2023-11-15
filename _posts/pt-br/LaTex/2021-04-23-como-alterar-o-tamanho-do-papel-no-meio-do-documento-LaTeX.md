---
layout: post
lang: pt-BR
title: "Como alterar o tamanho do papel no meio do documento LaTeX"
date: 2021-04-23 18:00:00 -0400
description: "Neste artigo você descobre como alterar o tamanho do papel no meio do documento LaTeX."
image: "/assets/LaTeX/thumb/thumb-alterar-tamanho-do-papel-no-meio-do-documento-LaTeX.jpg"
category: LaTeX
tags: LaTeX
---

Já se perguntou como alterar o tamanho do papel no meio do documento LaTeX?

<!-- Youtube Video -->
<a href="https://www.youtube.com/watch?v=cRNMtmYU0FM" target="_blank">
  ![Thumbnail of youtube video Alterar do tamanho do papel no meio do documento LaTeX]({{ "/assets/LaTeX/thumb-youtube-alterar-tamanho-do-papel-no-meio-do-documento-LaTeX.jpg" | relative_url }} "Assistir no YouTube")
</a>

Se você quer alterar o tamanho de um documento pra imprimir uma só página diferente do restante do documento.

Por exemplo, você está escrevendo um documento em papel de dimensão A4 mas precisa incluir anexos em uma folha de dimensão A3.

Para fazer essa alteração da dimensão das folhas você precisa compilar com o pdfLaTeX ou o XeLaTeX.

```TeX
\documentclass[12pt,a4paper]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage{lipsum}

\begin{document}
\section{Conteúdo}
Conteúdo em A4

\newpage % Alteração da dimensão da página PDF a partir desse ponto
\pdfpag\newidth=297mm
\pdfpageheight=420mm

\section*{Anexos}
  Conteúdo em A3

\end{document}
```

Os comandos `\pdfpag\newidth` e `\pdfpageheight` especificam a largura e altura da folha do PDF.

Contudo, a área de texto não será alterada, respectivamente.

## Alteração do tamanho da página com o pacote typearea

Outra maneira de alterar o tamanho do papel no meio do documento LaTeX é usando o pacote **typearea**.

O código que você precisa pra usar esse pacote é:

```TeX
\documentclass[12pt,a4paper]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage[DIV=15]{typearea}

\begin{document}
\section{Conteúdo}
Conteúdo em A4

\newpage \KOMAoptions{paper=a3}
\recalctypearea

\section*{Anexos}
Conteúdo em A3

\end{document}
```

Diferente do que você viu no começo deste artigo, com o pacote **typearea** definimos uma área para o texto ser gerado.

Você vai definir essa área com o comando **[DIV=fator]**.

O **fator** desse comando é o que define a área de texto e das margens. Quanto maior o fator menor são as margens.

Já o comando `\KOMAoptions{paper=a3}` indica que o conteúdo abaixo dele estará em um papel de dimensão A3 e o comando `\recalctypearea` confirma essa mudança recalculando a área de texto.

Para mais informações sobre o pacote, leia a sua <a href="https://www.ctan.org/pkg/typearea" target="_blank">documentação</a>.

{%- include end_article.html -%}
