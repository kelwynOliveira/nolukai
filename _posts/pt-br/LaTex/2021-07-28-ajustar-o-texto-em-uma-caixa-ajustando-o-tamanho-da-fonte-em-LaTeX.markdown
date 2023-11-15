---
layout: post
lang: pt-BR
title: "Ajustar o texto em uma caixa com ajuste do tamanho da fonte em LaTeX"
date: 2021-07-28 18:00:00 -0400
description: "Neste artigo você descobre como ajustar o texto em uma caixa com ajuste do tamanho da fonte em LaTeX."
image: "/assets/LaTeX/thumb/thumb-latex-5.jpg"
category: LaTeX
tags: LaTeX
---

Se o seu objetivo é criar uma caixa de altura e largura específica e fazer com que o texto dentro dele se ajuste para ocupar todo esse espaço, fazendo com que o tamanho do texto aumente ou diminua automaticamente, então a solução está aqui.

O código abaixo faz uso do pacote `enivron` que oferece o ambiente `fitbox`.

```TeX
\begin{fitbox}{largura}{altura}
  conteúdo
\end{fitbox}
```

Onde em `{largura}` informamos a largura da caixa e em `{altura}` a altura da caixa.

O código abaixo insere um texto numa caixa de 7cm de largura por 300pt:

```TeX
\documentclass{article}
\usepackage{lmodern}
\usepackage{environ}
\usepackage{lipsum}
\newdimen\fontdim
\newdimen\upperfontdim
\newdimen\lowerfontdim
\newif\ifmoreiterations
\fontdim12pt\makeatletter
\newEnviron{fitbox}[2]{ %
  \def\buildbox{ %
    \setbox0\vbox{\hbox{\minipage{#1}%
      \fontsize{\fontdim}{1.2\fontdim}%
      \selectfont%
      \stuff%
    \endminipage}}%
    \dimen@\ht0
    \advance\dimen@\dp0
  }
  \def\stuff{\BODY}% Armazena o corpo do ambiente
  \buildbox
  % Calcular limites superior e inferior
  \ifdim\dimen@&gt;#2
    \loop
      \fontdim.5\fontdim % Reduz o tamanho da fonte pela metade
      \buildbox
    \ifdim\dimen@&lt;#2 \repeat
    \lowerfontdim\fontdim
    \upperfontdim2\fontdim
    \fontdim1.5\fontdim
  \else
    \loop
      \fontdim2\fontdim % Dobra o tamanho da fonte
      \buildbox
    \ifdim\dimen@&gt;#2 \repeat
    \upperfontdim\fontdim
    \lowerfontdim.5\fontdim
    \fontdim.75\fontdim
  \fi
  % Tenta encontrar o tamanho ideal
  \loop
    %\message{Bounds: \the\lowerfontdim\space
    %         \the\fontdim\space \the\upperfontdim^^J}
    \buildbox
    \ifdim\dimen@&lt;#2
      \moreiterationstrue
      \upperfontdim\fontdim
      \advance\fontdim\lowerfontdim
      \fontdim.5\fontdim
    \else
      \advance\dimen@-#2
      \ifdim\dimen@&gt;10pt
        \lowerfontdim\fontdim
        \advance\fontdim\upperfontdim
        \fontdim.5\fontdim
        \dimen@\upperfontdim
        \advance\dimen@-\lowerfontdim
        \ifdim\dimen@&gt;.2pt
          \moreiterationsfalse
        \else
          \moreiterationstrue
        \fi
      \else
        \moreiterationsfalse
      \fi
    \fi
  \ifmoreiterations \repeat
  \box0% Escreve o conteúdo
}
\makeatother
\begin{document}
    \lipsum[1]
    \begin{fitbox}{7cm}{300pt}
      \lipsum[1-1]
    \end{fitbox}
    \lipsum[2]
\end{document}
```

![texto central ajustado para caber dentro de uma caixa de 7cm x 300pt com o tamanho do texto ajustado para caber na caixa]({{ "/assets/LaTeX/resultado-do-ajuste-de-texto-em-uma-caixa-com-ajuste-do-tamanho-da-fonte-em-LaTeX.jpg" | relative_url }} "texto central ajustado para caber dentro de uma caixa de 7cm x 300pt com o tamanho do texto ajustado para caber na caixa")

{%- include end_article.html -%}
