---
layout: post
lang: pt-BR
title: "Como alterar o espaçamento vertical entre os itens da lista no LaTeX"
date: 2020-08-28 18:00:00 -0400
description: "Neste artigo você descobre como alterar o espaçamento vertical entre os itens."
image: "/assets/LaTeX/thumb/thumb-latex-5.jpg"
category: LaTeX
tags: LaTeX
---

Para realizar a alteração do espaçamento vertical entre os itens da lista utilizaremos o pacote <strong>enumitem</strong>. Esse pacote tem muitas funcionalidades além de configurar o espaçamento vertical, então talvez valha a pena dar uma olhada em sua <a href="https://www.ctan.org/pkg/enumitem\" target="_blank">documentação</a>.

O código abaixo retira os espaçamentos entre os itens da lista, mas permanece com o espaçamento superior, das laterais e inferior.

```TeX
\documentclass{article}
\usepackage{lipsum}
\usepackage{enumitem}
%\setlist{nosep} % Retira todos os espaçamentos
\setlist{noitemsep} % cria espaçamento ao redor da lista (superior, laterais e inferior)

\begin{document}
\lipsum[1]
\begin{itemize}
    \item \lipsum[1][1]
    \item \lipsum[1][1-2]
    \item \lipsum[1][2]
    \item \lipsum[2][1]
\end{itemize}
\lipsum[1]
\end{document}
```

![resultado da alteração de espaçamento dos itens de listas]({{ "/assets/LaTeX/alteracao-do-espaco-de-itens-da-lista.jpg" | relative_url }} "resultado da alteração de espaçamento dos itens de listas")

Você também pode configurar o espaçamento de um nível específico ou de uma lista específica. Veja o código abaixo:

```TeX
\documentclass{article}
\usepackage{lipsum}
\usepackage{enumitem}
\setlist[2]{noitemsep} % configura o itemsep e parsep de todas as listas de nível 2 para espaçamento zero
\setenumerate{noitemsep} % configura a separação apenas das listas do tipo enumerate

\begin{document}
\lipsum[1][1-4]
\begin{itemize}
    \item \lipsum[1][1]
    \item \lipsum[1][1-2]
    \begin{itemize}
        \item \lipsum[1][1]
        \item \lipsum[1][1-2]
    \end{itemize}
    \item \lipsum[1][2]
\end{itemize}
\lipsum[1][1-4]
\begin{enumerate}
    \item \lipsum[1][1]
    \item \lipsum[1][1-2]
    \item \lipsum[1][2]
\end{enumerate}
\lipsum[1][1-4]
\begin{description}[noitemsep] % configura o espaçamento apenas para esta lista
    \item[x1] \lipsum[1][1]
    \item[x2] \lipsum[1][1-2]
    \item[x3] \lipsum[1][2]
    \item[x4] \lipsum[2][1]
\end{description}
\end{document}
```

![resultado da alteração de espaçamento dos itens de listas específicas]({{ "/assets/LaTeX/alteracao-do-espaco-de-itens-da-lista-especificamente.jpg" | relative_url }} "resultado da alteração de espaçamento dos itens de listas específicas")

{%- include end_article.html -%}
