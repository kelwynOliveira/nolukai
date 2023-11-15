---
layout: post
lang: pt-BR
title: "Como criar tabelas de largura fixa no LaTeX"
date: 2020-08-02 18:00:00 -0400
description: "Neste artigo você descobre como criar tabelas de largura fixa no LaTeX."
image: "/assets/LaTeX/thumb/thumb-latex-2.jpg"
category: LaTeX
tags: LaTeX
---

## O ambiente tabularx

A primeira opção é criar uma tabela utilizando o ambiente `tabularx` (insira o pacote tabularx no preâmbulo do seu documento). Este ambiente permite estabelecer uma largura total para a tabela e utiliza a coluna no formato do tipo X.

Todas as colunas que forem especificadas como do tipo X terão suas larguras iguais.

No código abaixo a tabela possui um comprimento total de 10cm e a primeira e segunda coluna possuem o mesmo comprimento.

```TeX
\documentclass[12pt]{article}
\usepackage{tabularx}\begin{document}
    \centering
    \begin{table}[!htbp]
        \begin{tabularx}{10cm}{|X|X|l|}
            \hline
            texto &amp; texto &amp; texto\\
            \hline
            texto &amp; texto &amp; texto\\
            \hline
            texto &amp; texto &amp; texto\\
            \hline
        \end{tabularx}
    \end{table}
\end{document}
```

![Exemplo de uso do tabularx]({{ "/assets/LaTeX/exemplo-Tabularx.jpg" | relative_url }} "Exemplo de uso do tabularx")

## Especificar o comprimento de cada coluna

Caso a sua intenção não seja criar uma tabela de comprimento fixo, mas sim de uma coluna você pode recorrer ao uso do pacote `array`.

Assim você pode informar o alinhamento que deseja para o conteúdo dentro da coluna. Alguns argumentos de coluna podem ser `p{largura}` (justifica o conteúdo), `m{largura}` (coloca o conteúdo no centro), `b{largura}` (alinha o conteúdo na base da célula).

Como você viu não existe a opção par alinhar à esquerda ou direita. Então utilizaremos a função `n\newcolumntype` para criar as nossas.

```TeX
\documentclass[12pt]{article}
\usepackage{array}
\usepackage{tabularx}
\newcolumntype{E}[1]{&gt;{\raggedright\let
\newline\\\arraybackslash\hspace{0pt}}m{#1}} %Alinha na esquerda

\newcolumntype{C}[1]{&gt;{\centering\let
\newline\\\arraybackslash\hspace{0pt}}m{#1}}%Alinha no centro

\newcolumntype{D}[1]{&gt;{\raggedleft\let
\newline\\\arraybackslash\hspace{0pt}}m{#1}}%Alinha na direita\begin{document}
    \centering
    \begin{table}[!htbp]
        \begin{tabular}{|E{3cm}|C{2cm}|D{4cm}|}
            \hline
            texto &amp; texto &amp; texto\\
            \hline
            texto &amp; texto &amp; texto\\
            \hline
            texto &amp; texto &amp; texto\\
            \hline
        \end{tabular}
    \end{table}
\end{document}
```

![Exemplo de como criar uma tabela de largura fixa no LaTeX]({{ "/assets/LaTeX/criar-tabela-de-largura-fixa.jpg" | relative_url }} "Exemplo de como criar uma tabela de largura fixa no LaTeX")

{%- include end_article.html -%}
