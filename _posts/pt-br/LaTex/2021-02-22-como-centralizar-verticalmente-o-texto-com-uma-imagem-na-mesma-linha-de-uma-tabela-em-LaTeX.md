---
layout: post
lang: pt-BR
title: "Como centralizar verticalmente o texto com uma imagem na mesma linha de uma tabela em LaTeX"
date: 2021-02-22 18:00:00 -0400
description: "Neste artigo você descobre como centralizar verticalmente o texto com uma imagem na mesma linha de uma tabela em LaTeX."
image: "/assets/LaTeX/thumb/thumb-latex-5.jpg"
category: LaTeX
tags: LaTeX
---

Quando colocamos uma imagem em uma célula de uma tabela o seu alinhamento é por base a parte inferior da célula.

![Posicionamento de legendas na figura LaTeX]({{ "/assets/LaTeX/posicionamento-de-legendas-na-figura-LaTeX.jpg" | relative_url }} "Posicionamento de legendas na figura LaTeX")

```TeX
\documentclass[12pt]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage{graphicx}

\begin{document}
  \centering
  \begin{tabular}{*3c}
  texto & \includegraphics[width=.5\linewidth]{imagem1.jpg} & texto\\
  texto & texto & texto
  \end{tabular}
\end{document}
```

Para conseguir alinhar de forma vertical você pode [criar uma caixa]({{ "quais-sao-os-diferentes-tipos-de-caixas-no-LaTeX" | relative_url }}) com o comando `\raisebox`.

Com esse comando podemos informar uma profundidade para a imagem, nesse caso metade da altura da caixa (`-0.5\height`).

```TeX
\documentclass[12pt]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage{graphicx}

\begin{document}
  \centering
  \begin{tabular}{*3c}
  texto & \raisebox{-0.5\height}{\includegraphics[width=.5\linewidth]{imagem1.jpg}} & texto\\
  texto & texto & texto
  \end{tabular}
\end{document}
```

![Posicionamento de legendas nas figuras LaTeX]({{ "/assets/LaTeX/posicionamento-de-legendas-nas-figuras-LaTeX.jpg" | relative_url }} "Posicionamento de legendas nas figuras LaTeX")

{%- include end_article.html -%}
