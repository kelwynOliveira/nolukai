---
layout: post
lang: pt-BR
title: "Como dividir uma equação em duas ou mais linhas no LaTeX"
date: 2020-10-15 18:00:00 -0400
description: "Neste artigo você descobre como dividir uma equação em duas ou mais linhas no LaTeX."
image: "/assets/LaTeX/thumb/thumb-latex-5.jpg"
category: LaTeX
tags: LaTeX
---

Fazer com que uma equação longa ocupe mais de uma linha pode ser mais simples do que você imagina, tudo vai depender de como você deseja que a equação seja exibida, o seu alinhamento.

Para ter mais liberdade no hora de definir o local onde ocorrerá as quebras de linhas da equação use o ambiente `eqnarray`, a sua estrutura é parecida com a da criação de uma tabela, exceto que não é preciso informar o tipo de alinhamento. Seu alinhamento padrão é a esquerda.

O comando `\nonumber` é utilizado para não gerar o número da equação para determinada linha.

```TeX
\documentclass{article}

\begin{document}
\begin{eqnarray}
\cos x &= & 1 -\frac{x^{2}}{2!} + \frac{x^{4}}{4!} - \frac{x^{6}}{6!} + \frac{x^{8}}{8!} - {}
\nonumber\\
&  & {} - \frac{x^{10}}{10!} + \frac{x^{12}}{12!} - \frac{x^{14}}{14!} +\frac{x^{16}}{16!} - {}
\nonumber\\
&  & {}  - \frac{x^{18}}{18!} + \frac{x^{20}}{20!} - \frac{x^{22}}{22!} + \frac{x^{24}}{24!} - {}
\nonumber\\
&  & {} - \frac{x^{26}}{26!} + \ldots
\end{eqnarray}
\end{document}
```

$$
\begin{eqnarray}
\cos x &= & 1 -\frac{x^{2}}{2!} + \frac{x^{4}}{4!} - \frac{x^{6}}{6!} + \frac{x^{8}}{8!} - {}
\nonumber\\
&  & {} - \frac{x^{10}}{10!} + \frac{x^{12}}{12!} - \frac{x^{14}}{14!} +\frac{x^{16}}{16!} - {}
\nonumber\\
&  & {}  - \frac{x^{18}}{18!} + \frac{x^{20}}{20!} - \frac{x^{22}}{22!} + \frac{x^{24}}{24!} - {}
\nonumber\\
&  & {} - \frac{x^{26}}{26!} + \ldots
\end{eqnarray}
$$

Caso você não se importe com o alinhamento e queira que as linhas sejam quebradas automaticamente utilize o pacote `breqn` e o envolva a equação no ambiente `dmath`.

```TeX
\documentclass{article}
\usepackage{breqn}

\begin{document}
\begin{dmath}
\cos x = 1 -\frac{x^{2}}{2!} + \frac{x^{4}}{4!} - \frac{x^{6}}{6!} + \frac{x^{8}}{8!} - \frac{x^{10}}{10!} + \frac{x^{12}}{12!} - \frac{x^{14}}{14!} + \frac{x^{16}}{16!} - \frac{x^{18}}{18!} + \frac{x^{20}}{20!} - \frac{x^{22}}{22!} + \frac{x^{24}}{24!} - \frac{x^{26}}{26!} + \ldots
\end{dmath}
\end{document}
```

$$
\begin{eqnarray}
\cos x &= & 1 -\frac{x^{2}}{2!} + \frac{x^{4}}{4!} - \frac{x^{6}}{6!} + \frac{x^{8}}{8!}
\nonumber\\
&  & {} - \frac{x^{10}}{10!} + \frac{x^{12}}{12!} - \frac{x^{14}}{14!} +\frac{x^{16}}{16!}
\nonumber\\
&  & {}  - \frac{x^{18}}{18!} + \frac{x^{20}}{20!} - \frac{x^{22}}{22!} + \frac{x^{24}}{24!}
\nonumber\\
&  & {} - \frac{x^{26}}{26!} + \ldots
\end{eqnarray}
$$

{%- include end_article.html -%}
