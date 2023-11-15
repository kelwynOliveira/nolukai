---
layout: post
lang: pt-BR
title: "Como fazer um mini sumário do capítulo em LaTeX"
date: 2021-03-04 18:00:00 -0400
description: "Neste artigo você descobre como fazer um mini sumário do capítulo em LaTeX."
image: "/assets/LaTeX/thumb/thumb-latex-6.jpg"
category: LaTeX
tags: LaTeX
---

Em alguns livros, encontramos um mini sumário que apresenta as seções e subseções por capítulo. Agora você vai aprender como fazer isso no LaTeX, com o pacote `minitoc` (<a href="https://www.ctan.org/pkg/minitoc" target="_blank">documentação</a>):

```TeX
\documentclass[12pt,a4paper]{book}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage{lipsum}\usepackage{minitoc}
\mtcselectlanguage{brazil} % Tradução do mini sumário\begin{document}
	\dominitoc[c] % Inicialização do mini sumário
	\tableofcontents

	\chapter{O início}
	\minitoc % Criação do mini sumário

	\section{Seção 1}
	\lipsum[1]
	\section{Seção 2}
	\lipsum[1]
	\subsection{Subseção 1}
	\lipsum[1]

	\chapter{O final}
	\minitoc % Criação do mini sumário

	\section{Seção 1}
	\lipsum[1]
	\section{Seção 2}
	\lipsum[1]
	\subsection{Subseção 1}
	\lipsum[1]

\end{document}
```

Veja como o LaTeX faz a compilação desse mini sumário de capítulo:

![Sumário do capítulo no LaTeX]({{ "/assets/LaTeX/sumario-do-capitulo-no-latex-1.jpg" | relative_url }} "Sumário do capítulo no LaTeX")

Perceba que, no preâmbulo do documento, foi inserido o comando `\mtcselectlanguage{brazil}`.

Esse comando traduz o mini sumário para o português do Brasil, e usa o mesmo parâmetro do pacote babel.

Mas para que esse pacote funcione, você precisa adicionar os comandos `\dominitoc` e `\tableofcontents`.

## Parâmetros opcionais para o `\dominitoc`

Você pode escolher a posição do título do mini sumário do seu capítulo em LaTeX utilizando os seguintes códigos:

- [l] - posiciona o título do lado esquerdo (left), é o padrão e será acionado caso você não atribua nenhum dos demais ao `\dominitoc`;
- [c] - centraliza o título (center);
- [r] - posiciona o título do lado direito (right);
- [e] ou [n] - remove o título (empty / no title).

O comando `\minitoc` toma como referência o capítulo em que ele está para verificar as hierarquias (section, subsection, etc) e então criar o mini sumário.

## Outros comandos

- `\setcounter{minitocdepht}{profundidade}` - especifica a profundidade da hierarquia do mini sumário, 1 para seções, 2 para subseções, 3 para sub subseções, e etc.;
- `\nomtocrule` - remove as linhas horizontais do mini sumário;
- `\nomtocpagenumbers` - remove a numeração do mini sumário;
- `\undottedmtctrue` - remove os pontos que separam o nome do capítulo da numeração.

## Para lista de figuras e tabelas

No lugar de usar o `\dominitoc`, para criar mini sumários dentro de capítulos, você pode usar:

- `\dominilof `ou `\minilof` - para criar uma lista de figuras
- `\dominilot` ou `\minilot` - para criar uma lista de tabelas

## LaTeX na classe article

Se você estiver utilizando o LaTeX na classe article (que não aceita capítulos), você pode fazer um mini sumário com `\dosecttoc` e `\secttoc`.

{%- include end_article.html -%}
