---
layout: post
lang: pt-BR
title: "Como inserir lista de figuras e lista de tabelas no LaTeX"
date: 2020-06-01 18:00:00 -0400
description: "Neste artigo você descobre como inserir lista de figuras e lista de tabelas no LaTeX."
image: "/assets/LaTeX/thumb/thumb-latex-1.jpg"
category: LaTeX
tags: LaTeX
---

Em muitos livros, artigos, trabalhos encontramos uma lista de figuras e lista de tabelas. Uma das grandes vantagens do LaTeX é a capacidade de ele gerar essas listas apenas com um comando para cada um deles, esse comandos vão coletar todas as figuras e/ou tabelas no trabalho e automaticamente gerar suas respectivas listas.

Para que seja inserida a lista de figuras basta adicionar no local do arquivo onde se deseja que a lista apareça o comando `\listoffigures` (lof), já para inserir a lista de tabelas deve-se inserir o comando `\listoftables` (lot). Esses comandos são utilizados da mesma forma que o `\listofcontents` (loc)usado para criar o sumário do trabralho.

Quando inserido o comando de inserção de lista de figuras e tabelas é feita a coleta de todas as legendas de figuras e tabelas geradas com o comando `\caption` e então ele é incluído na sua respectiva lista.

## Como alterar o nome da legenda que aparece na lista de figuras/tabelas quando a legenda é muito grande

É muito possível que a sua legenda seja longa o que resultaria em uma lista de figuras ou lista de tabelas ainda mais longa. Outra vantagem do LaTeX é que ele oferece a opção de dar uma legenda diferente para as imagens e tabelas que vão aparecer na lista de figuras ou lista de tabelas e o que vai efetivamente aparecer no item de figura/tabela.

A configuração da legenda que vai aparecer na lista e na própria figura/tabela é feita através do comando `\caption`, esse comando pode receber até dois parâmetros, um parâmetro opcional entre colchetes que é onde você inclui a legenda que irá para a lista de figuras/tabelas, e também recebe um parâmetro obrigatório que é onde você deve informar a legenda que aparecerá no item de figura/tabela. O comando em sua forma completa é:

```TeX
\caption[parâmetro opcional]{parâmetro obrigatório}
\caption[legenda curta em lof/lot]{legenda longa que vai aparecer na figura/tabela}
```

O parâmetro opcional entre colchetes, como o próprio nome sugere, não precisa ser inserido, quando isso é feito a legenda que vai aparecer na lista de figuras ou lista de tabelas será a legenda entre as chaves.

```TeX
\caption{parâmetro obrigatório}
\caption{legenda longa que vai aparecer na figura/tabela e na lof/lot}
```

## Como alterar o nome da lista de figuras/tabelas

Por padrão o título que aparece na lista de figuras é List of Figures, isso é, caso você não esteja usando um pacote que especifique a língua utilizada no seu documento como o `\uspackage[brazil]{babel}`. Neste caso em que é utilizado o pacote que especifica o português do Brasil como língua do trabalho o título da lista de figuras seria traduzida para Lista de Figuras.

Para alterar o padrão em um título específico é preciso reescrever o comando que nomeia a lista de figuras. A alteração deve ser feita antes de chamar o comando `\listoffigures` como apresentado abaixo:

```TeX
\renewcommand\listfigurename{Lista de Imagens}
\listoffigures
```

Essa lógica é aplicável para a lista de tabelas da mesma forma que é para a lista de figuras, mas invés de `\listfigurename` você deve utilizar `\listtablename`.

{%- include end_article.html -%}
