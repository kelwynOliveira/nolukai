---
layout: post
lang: pt-BR
title: "Crie capítulos e seções não numeradas no LaTeX"
date: 2020-10-21 18:00:00 -0400
description: "Neste artigo você descobre com crie capítulos e seções não numeradas no LaTeX."
image: "/assets/LaTeX/thumb/thumb-capitulos-e-secoes-nao-numeradas-no-LaTeX-e-que-aparecam-no-sumario-e-cabecalho.jpg"
category: LaTeX
tags: LaTeX
---

Apesar de não ser o padrão, você pode inserir capítulos e seções não numeradas no LaTeX.

Em alguns casos, como na introdução de documentos, é comum que a gente insira essa divisão sem uma numeração.

<!-- Youtube Video -->
<a href="https://www.youtube.com/watch?v=ACEGcMAdyro" target="_blank">
  ![Thumbnail of youtube video Capítulos e seções não numeradas no LaTeX - e que apareçam no sumário e cabeçalho]({{ "/assets/LaTeX/thumb-youtube-capitulos-e-secoes-nao-numeradas-no-LaTeX-e-que-aparecam-no-sumario-e-cabecalho.jpg" | relative_url }} "Assistir no YouTube")
</a>

## Como criar itens não numerados no LaTeX

Independente de qual item (capítulo, seção, subseção, etc.) você queira criar sem uma numeração, o comando é sempre o mesmo e bem simples.

Você só precisa adicionar um `*` (asterisco) antes da abertura das chaves do comando.

Ou seja, o código seria:

```TeX
\chapter*{Introdução}
\section*{Prólogo}
```

## Como inserir itens não numerados no sumário do LaTeX

Por padrão, os itens não numerados no LaTeX não aparecem no sumário do documento se ele for gerado com o comando `\tableofcontents`.

Para incluir um item não numerado no sumário do seu documento, você precisa inserir o comando `\addcontentsline` logo depois da seção.

Então esse trecho do código fica assim:

```TeX
\chapter*{introdução}
\addcontentsline{toc}{chapter}{Introdução}
```

O argumento `{toc}` diz que a seção inserida faz parte do unidade de Table Of Contents (o equivalente a sumário, em inglês).

Em outras palavras, é do argumento `{toc}` que os capítulos, seções, etc são extraídos para a criação do sumário.

Enquanto o segundo argumento, `{chapter}`, informa qual é o tipo de seção.

Entre os tipos de seção mais comuns, temos:

- **part**, para partes;
- **chapter**, para capítulos;
- **section**, para seções.

E o último argumento entre as chaves é utilizado para inserir o nome que vai aparecer escrito no sumário.

No caso do exemplo acima, o nome seria **Introdução.**

### Veja um exemplo prático

Então de acordo com o que você já viu até aqui, o código completo para inserir uma introdução, por exemplo, seria:

```TeX
\documentclass[12pt, a4paper]{report}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}

\begin{document}
  \tableofcontents
  \chapter*{Introdução}
  \addcontentsline{toc}{chapter}{Introdução}
  \chapter{Capítulo 1}
  \chapter{Capítulo 2}
\end{document}
```

![Criação de capítulos e seções não numeradas e inserção no TOC e cabeçalho no LaTeX]({{ "/assets/LaTeX/criacao-de-capitulos-secoes-nao-numeradas-e-insercao-no-TOC-e-cabecalho-no-LaTeX.jpg" | relative_url }} "Criação de capítulos e seções não numeradas e inserção no TOC e cabeçalho no LaTeX")

## Como inserir itens não numerados no cabeçalho do LaTeX

Além de não serem exibidos no sumário, o nome das seções não numeradas também não aparecem no cabeçalho do documento em LaTeX.

Para que esses itens sejam inseridos, você pode usar um destes dois comandos logo depois do item (capítulo, seção, etc.):

- `\markboth{Título1}{Título2}`
- `\markright{Título2}`

Considerando um documento de dois lados, você escolhe o **{Título1}**, que é inserido no cabeçalho das páginas pares (esquerda), e o **{Título2}**, no das páginas ímpares (direita).

Além disso, para colocar todo o conteúdo do título do item em maiúsculo, basta usar o comando `\MakeUppercase{...}`.

Então, o código que você pode ver abaixo insere o título **INTRODUÇÃO**cabeçalhos apenas das páginas pares.

```TeX
\documentclass[12pt, a4paper]{book}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}

\begin{document}
  \tableofcontents
  \chapter*{Introdução}
  \addcontentsline{toc}{chapter}{Introdução}
  \markboth{\MakeUppercase{Introdução}}{}[...]
\end{document}
```

E essa é a forma correta de inserir capítulos e seções não numeradas no LaTeX!

{%- include end_article.html -%}
