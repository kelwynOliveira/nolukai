---
layout: post
lang: pt-BR
title: "Como colocar a legenda ao lado da figura no LaTeX"
date: 2021-03-18 18:00:00 -0400
description: "Neste artigo você descobre como colocar a legenda ao lado da figura no LaTeX."
image: "/assets/LaTeX/thumb/thumb-latex-7.jpg"
category: LaTeX
tags: LaTeX
---

Normalmente as legendas ficam abaixo da figura ou da tabela, mas agora vamos descobrir como colocar a legenda ao lado no LaTeX.

Para fazer isso precisaremos do pacote **floatrow** (<a href="https://www.ctan.org/pkg/floatrow" target="_blank">documentação</a>) para então utilizarmos os comandos **\floatbox** e **\capbeside**.

```TeX
\floatbox[preâmbulo]{tipo do caption}[largura][altura][alinhamento vertical]{caption com ou sem label}{conteúdo(imagem)}
```

O comando **\capbeside** é utilizado no **[preâmblo]** para informar a posição e a largura do caption.

No exemplo abaixo a legenda fica ao lado esquerdo da figura e alinhado com o topo:

```TeX
\documentclass[12pt]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage[demo]{graphicx}
\usepackage{floatrow}

\begin{document}

\begin{figure}
\floatbox[%
    {\capbeside\thisfloatsetup{
        capbesideposition={left,top},
        capbesidewidth=4cm}
    }]{figure}[\FBwidth]
    {
        \caption{Esta é a legenda da figura}
        \label{fig:figura}
    }
    {\includegraphics[width=5cm]{figura}}
\end{figure}

end{document}
```

![Legenda ao lado de uma figura]({{ "/assets/LaTeX/Legenda-ao-lado-de-uma-figura.jpg" | relative_url }} "Legenda ao lado de uma figura")

Para colocar a legenda do lado direito basta escrever **right** no lugar de **left** em **capbesideposition={left,top}**.

{%- include end_article.html -%}
