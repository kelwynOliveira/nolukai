---
layout: post
lang: pt-BR
title: "Como escrever sobrescrito e subscritos nos modos de texto e matemático do LaTeX"
date: 2020-10-27 18:00:00 -0400
description: "Neste artigo você descobre como escrever sobrescrito e subscritos nos modos de texto e matemático do LaTeX."
image: "/assets/LaTeX/thumb/thumb-latex-5.jpg"
category: LaTeX
tags: LaTeX
---

O uso de sub e sobre escritos é mais comum em expressões matemáticas, mas também existem os casos em que você deseja que o seu texto tenha essa configuração.

## Subscrito e sobrescrito no modo matemático do LaTeX

Para o caso do ambiente matemático é bem simples.

Informamos que um item deve estar sobrescrito no modo matemático com o caractere ^ (circunflexo) colocado antes do item que se deseja suspender.

Para informar que um item deve estar subscrito no modo matemático utilizamos o caractere \_ (barra inferior) colocado antes do item que se deseja inferiorizar.

Você pode fazer a delimitação dos itens a serem sub e sobrescritos apenas envolvendo o item entre chaves.

```TeX
\begin{document}
  \[ \int\limits_0^1 x^2 + y^2 \ dx \]
  \[ (a^n)^{r+s} = a^{nr+ns}  \]
\end{document}
```

$$
   \int\limits_0^1 x^2 + y^2 \ dx \]
  \[ (a^n)^{r+s} = a^{nr+ns}
$$

## Subscrito e sobrescrito no modo de texto do LaTeX

O LaTeX nos permite gerar textos sub e sobrescritos com os comandos <strong>\textsubscript</strong> e <strong>\textsuperscript</strong>.

```TeX
\begin{document}

  Texto\textsuperscript{sobrescrito}

  Texto\textsubscript{subscrito}

\end{document}
```

![Subscrito e sobrescrito no modo matemático do LaTeX]({{ "/assets/LaTeX/subscrito-e-sobrescrito-no-modo-de-texto-do-LaTeX.jpg" | relative_url }} "Subscrito e sobrescrito no modo matemático do LaTeX")

{%- include end_article.html -%}
