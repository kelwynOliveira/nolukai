---
layout: post
lang: pt-BR
title: "Como usar uma fonte específica em apenas uma parte do texto em LaTeX"
date: 2020-07-13 18:00:00 -0400
description: "Neste artigo você descobre como usar uma fonte específica em apenas uma parte do texto em LaTeX."
image: "/assets/LaTeX/thumb/thumb-latex-5.jpg"
category: LaTeX
tags: LaTeX
---

Colocar uma parte do texto com uma fonte específica pode ser bem simples.

Primeiro você precisa saber qual o nome da fonte. Você pode encontrar fontes no catálogo do site <a href="https://tug.org/FontCatalogue/" target="_blank">https://tug.org/FontCatalogue/</a>.

Basta clicar no tipo de fonte que deseja e selecionar.

Para definir as fontes padrões, no preâmbulo escreva:

```TeX
\setmainfont{nome da fonte} %Fonte principal
\setromanfont{nome da fonte} %Fonte da família roman/serifada
\setsansfont{nome da fonte} %Fonte da família sem serifa
\setmonofont{nome da fonte} %Fonte da família mono espaçada
```

Você também pode reconfigurar as fontes de comandos como:

```TeX
\renewcommand{\sfdefault}{nome da fonte}
\renewcommand{\rmdefault}{nome da fonte}
\renewcommand{\ttdefault}{nome da fonte}
```

## Seleção da fonte para um texto específico

Caso a sua intenção seja alterar um pequeno trecho do seu texto utilize o comando:

```TeX
\fontfamily{nome da fonte}\selectfont
```

É interessante envolver essa instrução com o texto em um ambiente ou entre chaves.

Como exemplo, considere um trecho de texto com a fonte `Latin Modern` usando o código `lmdh`.

```TeX
\documentclass[12pt,a4paper]{article}
\usepackage[utf8]{inputenc}
\usepackage[brazil]{babel}
\usepackage{lmodern} % Pacote da fonte Latin Modern

\begin{document}
Este é um texto com fonte padrão.

{\fontfamily{lmdh}\selectfont
  Este é um texto com fonte Latin Modern
}.
\end{document}
```

![Resultado de como utilizar uma fnte específica no texto em LaTeX]({{ "/assets/LaTeX/specific-font-in-LaTeX.png" | relative_url }} "Resultado de como utilizar uma fnte específica no texto em LaTeX")

Abaixo uma tabela de pacotes e códigos de fontes:

| Fonte             | Pacote     | Código da família |
| ----------------- | ---------- | ----------------- |
| Latin Modern      | lmodern    | lmr               |
| Latin Modern      | lmodern    | lmdh              |
| Latin Modern      | lmodern    | lmss              |
| Latin Modern      | lmodern    | lmtt              |
| Bookman           | bookman    | pbk               |
| TeX Gyre Adventor | tgadventor | qag               |
| Helvetica         | helvet     | phv               |
| Courier           | courier    | pcr               |

<br>
{%- include end_article.html -%}
