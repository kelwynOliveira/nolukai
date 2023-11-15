---
layout: post
lang: pt-BR
title: "Como colocar a primeira linha da tabela em negrito no LaTeX"
date: 2021-02-20 18:00:00 -0400
description: "Neste artigo você descobre como colocar a primeira linha da tabela em negrito no LaTeX."
image: "/assets/LaTeX/thumb/thumb-latex-3.jpg"
category: LaTeX
tags: LaTeX
---

Uma das formas de destacar o cabeçalho da sua tabela no LaTeX é colocando a primeira linha dela em negrito.

Você pode fazer isso acontecer manualmente. Basta adicionar o comando para negritar em cada um dos termos da tabela. Por exemplo:

```TeX
\documentclass[12pt]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}

\begin{document}
\begin{tabular}{|c|c|c|}
  \hline
  \bfseries texto & \bfseries texto & \bfseries texto \\
  \hline
  texto & texto & texto \\
  \hline
  texto & texto & texto \\
  \hline
\end{tabular}
\end{document}
```

![Primeira linha da tabela em negrito no LaTeX]({{ "/assets/LaTeX/primeira-linha-da-tabela-em-negrito-no-LaTeX.jpg" | relative_url }} "Primeira linha da tabela em negrito no LaTeX")

O comando `\bfseries` na frente do texto da célula coloca o texto em negrito Mas imagine que você precisa fazer isso para uma tabela muito grande. Fica claro que isso é muito trabalhoso.

Então a melhor opção é criar os comandos que tornem isso mais fácil. Isso mesmo. **Criar** novos comandos.

## Criando um novo comando

Para criar os comandos, utilize o pacote `array`. Assim você pode usar o comando `>{...}` e também pode criar de tipos de colunas com o comando `\newcolumntype`.

- `>{instrução}` - é utilizado antes de l, c, r, p, m ou b e insere o conteúdo/código que está entre as chaves, no lugar de \"instrução\", logo no começo de cada entrada de coluna.

Por exemplo, se você quiser que todo o conteúdo da tabela fique em negrito, escreva:

```TeX
\documentclass[12pt]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage{array}

\begin{document}
\begin{tabular}{| >{\bfseries}c | >{\bfseries}c | >{\bfseries}c |}
  \hline
  texto & texto & texto \
  \hline
  texto & texto & texto \
  \hline
  texto & texto & texto \
  \hline
\end{tabular}
\end{document}
```

![Todos os itens da coluna da tabela em negrito no LaTeX]({{ "/assets/LaTeX/todos-os-itens-da-coluna-em-negrito-no-LaTex.jpg" | relative_url }} "Todos os itens da coluna da tabela em negrito no LaTeX")

- `\newcolumntype{marca}{instruções}` - permite a criação de um novo tipo de coluna. No lugar de \"marca\", insira apenas um símbolo ou letra para representar o tipo de coluna. E em \"instruções\", as instruções que definem o tipo de coluna.
  Veja como aquele mesmo exemplo que você viu antes fica mais fácil:

```TeX
\documentclass[12pt]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage{array}
\newcolumntype{j}{>{\bfseries}c}

\begin{document}
\begin{tabular}{|j|j|j|}
  \hline
  texto & texto & texto \
  \hline
  texto & texto & texto \
  \hline
  texto & texto & texto \
  \hline
\end{tabular}\end{document}
```

![Todos os itens da coluna da tabela em negrito no LaTeX]({{ "/assets/LaTeX/todos-os-itens-da-coluna-em-negrito-no-LaTex.jpg" | relative_url }} "Todos os itens da coluna da tabela em negrito no LaTeX")

Veja que com praticamente a mesma quantidade de linhas de código, conseguimos fazer todas as células ficarem em negrito.

Agora vamos fazer a primeira linha ficar em negrito usando o recurso `\global\let\currentrowstyle\relax`, que criamos.

```TeX
\documentclass[12pt]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage{array}

\begin{document}
\begin{tabular}{|>{\global\let\currentrowstyle\relax}c | >{\currentrowstyle}c | >{\currentrowstyle}c |}
  \hline
  \gdef\currentrowstyle{\bfseries}
  \bfseries texto & texto & texto \
  \hline
  texto & texto & texto \
  \hline
  texto & texto & texto \
  \hline
\end{tabular}\end{document}
```

O comando `\global\let\currentrowstyle\relax` diz que o estilo de linha atual (currentrowstyle) não deve fazer nada (relax).

Em `>{\currentrowstyle}` dizemos para utilizar o estilo estabelecido para a linha atual, que é alterada com a definição global para `\currentrowstyle` através de `\gdef\currentrowstyle{\bfseries}`.

Então o resultado disso é:

![Primeira linha da tabela em negrito no LaTeX]({{ "/assets/LaTeX/primeira-linha-da-tabela-em-negrito-no-LaTeX.jpg" | relative_url }} "Primeira linha da tabela em negrito no LaTeX")

Você pode simplificar esse código assim:

```TeX
\documentclass[12pt]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage{array}
\newcolumntype{+}{>{\global\let\currentrowstyle\relax}}
\newcolumntype{-}{>{\currentrowstyle}}
\newcommand{\rowstyle}[1]{\gdef\currentrowstyle{#1}#1}\begin{document}\begin{tabular}{| +c | -c | -c |}
\hline
\rowstyle{\bfseries}
texto & texto & texto \
\hline
texto & texto & texto \
\hline
texto & texto & texto \
\hline
\end{tabular}\end{document}
```

O comando `\rowstyle` foi criado para que fosse possível realizar a alteração do estilo da linha.

Mas caso você queira que outra linha tenha um estilo em itálico, você só precisará informar o estilo com o comando `\rowstyle` na linha desejada, por exemplo:

![Todos os itens da coluna da tabela em negrito no LaTeX]({{ "/assets/LaTeX/primeira-linha-da-tabela-em-negrito-no-LaTeX.jpg" | relative_url }} "Todos os itens da coluna da tabela em negrito no LaTeX")

```TeX
\documentclass[12pt]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage{array}
\newcolumntype{+}{>{\global\let\currentrowstyle\relax}}
\newcolumntype{-}{>{\currentrowstyle}}
\newcommand{\rowstyle}[1]{\gdef\currentrowstyle{#1}#1}

\begin{document}
\begin{tabular}{| +c | -c | -c |}
  \hline
  \rowstyle{\bfseries}
  texto & texto & texto \
  \hline
  texto & texto & texto \
  \hline
  \rowstyle{\itshape}
  texto & texto & texto \
  \hline
\end{tabular}
\end{document}
```

![Itens da linha em itálico no LaTeX]({{ "/assets/LaTeX/itens-da-linha-em-italico-no-latex-1.jpg" | relative_url }} "Itens da linha em itálico no LaTeX")

{%- include end_article.html -%}
