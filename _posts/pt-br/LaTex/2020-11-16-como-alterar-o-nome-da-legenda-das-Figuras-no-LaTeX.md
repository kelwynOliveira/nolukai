---
layout: post
lang: pt-BR
title: "Como alterar o nome da legenda das Figuras no LaTeX"
date: 2020-11-16 18:00:00 -0400
description: "Neste artigo você descobre como alterar o nome da legenda das Figuras no LaTeX."
image: "/assets/LaTeX/thumb/thumb-como-alterar-o-prefixo-das-legendas-de-figuras-no-latex.png"
category: LaTeX
tags: LaTeX
---

Quando utilizamos o comando `\caption` para gerar legendas no LaTeX, ele automaticamente insere o prefixo "Figura" no início da legenda. Mas em alguns casos não queremos esse prefixo na legenda. E aqui você vai entender como é possível alterar esse prefixo para qualquer outro nome na legenda das Figuras do seu código em LaTeX.

Não se preocupe. É muito simples.

<!-- Youtube Video -->
<div class="yt-video">
<iframe src="https://www.youtube.com/embed/ZqLbdgGIFC0?si=-ycLGefiv-w2k3Sp" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>

Você pode ver aqui embaixo todo o código padrão que usamos para gerar uma legenda no LaTeX, e que provavelmente é o código que você costuma usar também:

```TeX
\documentclass[12pt]{article}
\usepackage[brazil]{babel}
\usepackage{graphicx}

\begin{document}

\begin{figure}
    \centering
    \includegraphics[width=\linewidth]{example-image-a}
    \caption{Exemplo de figura}
    \label{fig:figura}
\end{figure}

\end{document}
```

![Imagem com legenda na figura LaTeX]({{ "/assets/LaTeX/imagem-com-legenda-figura.jpg" | relative_url }} "Imagem com legenda na figura LaTeX")

Observe que nesse código utilizamos o comando `\caption` para gerar a legenda da figura.

Fazendo isso, ao compilar o documento, o LaTeX vai gerar por padrão a legenda **Figura1: Exemplo de figura**.

Para alterar o prefixo **Figura** você vai precisar inserir um novo comando na parte principal (**main**) do seu código, ou seja, no preâmbulo do seu documento - antes do `\begin{document}`.

Ah! Verifique se você está usando o pacote babel ou não.

Caso não esteja utilizando o pacote babel, no preâmbulo do seu documento, insira o comando `\renewcommand`. Dentro dele, insira o `\figurename` e, em seguida, indique entre chaves o prefixo que você quer que apareça na legenda da figura.

Por exemplo, se você quiser alterar o prefixo padrão **Figura** para**Fig.**, basta inserir:

```TeX
\renewcommand{\figurename}{Fig.}
```

Caso esteja utilizando o pacote babel, utilize o código:

```TeX
\addto\captionsbrazil{
    \renewcommand{\figurename}{Fig.}
} % Substitua brazil pela linguagem em babel
```

Então, no caso de estar utilizando o pacote babel, o código completo para inserir o nosso prefixo de exemplo no documento seria:

```TeX
\documentclass[12pt]{article}
\usepackage[brazil]{babel}
\usepackage{graphicx}\addto\captionsbrazil{\renewcommand{\figurename}{Fig.}}

\begin{document}

\begin{figure}
    \centering
    \includegraphics[width=\linewidth]{example-image-a}
    \caption{Exemplo de figura}
    \label{fig:figura}
\end{figure}

\end{document}
```

![alteração do prefixo figura para fig no latex]({{ "/assets/LaTeX/alteracao-do-prefixo-figura-para-fig-no-latex.jpg" | relative_url }} "alteração do prefixo figura para fig no latex")

Lembre-se que utilizamos **Fig.** como exemplo, mas você pode escolher o nome que quiser.

{%- include end_article.html -%}
