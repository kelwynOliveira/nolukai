---
layout: post
lang: pt-BR
title: "Quais são as classes de documentos disponíveis no LaTeX? (documentclass)"
date: 2020-11-28 18:00:00 -0400
description: "Neste artigo você descobre quais são as classes de documentos disponíveis no LaTeX? (documentclass)."
image: "/assets/LaTeX/thumb/thumb-classes-de-documentos-no-LaTeX.png"
category: LaTeX
tags: LaTeX
channel-id: UCYUU9jqWR41rkRXBQHBdbtw
---

Conheça as classes de documentos disponíveis no LaTeX ou **documentclass**.

<!-- Youtube Video -->
<div class="yt-video">
<iframe src="https://www.youtube.com/embed/m3xnxEhVL-c?si=1weh-64DBaxtojCP" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>

{%- include subscribe-channel.html -%}


`\documentclass` é o primeiro comando a ser informado quando criamos um novo documento. É o comando que especifica qual é o tipo de documento que será escrito.

O código deve ser inserido seguindo esta ordem:

```TeX
\documentclass[opções]{classe}
```

A seguir, entenda quais são os tipos de classes e de opções que o LaTeX disponibiliza.

## Tipos de classes de documentos disponíveis

Existem várias classes de documentos disponíveis no LaTeX ou **documentclass** disponíveis pra você.

A lista abaixo apresenta algumas das classes de documentos que podem ser usadas. Algumas são muito conhecidas e bastante usadas, já outras poucos conhecem:

| Classe de documento | Função                                                                                                                             |
| ------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| article             | Para escrever artigos, relatórios curtos, ...                                                                                      |
| report              | Para escrever relatórios longos que possuam vários capítulos, livros pequenos, ...                                                 |
| book                | Para escrever livros                                                                                                               |
| letter              | Para escrever cartas                                                                                                               |
| memoir              | Para alterar sensivelmente a saída do documento. É baseado na classe book, mas você pode criar qualquer tipo de documento com ele. |
| slides              | Para criar slides                                                                                                                  |
| beamer              | Para criar apresentações                                                                                                           |
| minimal             | Para criar um documento mínimo definindo apenas um tamanho de página e fonte base. É usado principalmente para fins de depuração.  |
| proc                | Para criar um documento de procedimentos, sendo baseada na classe article.                                                         |

## Opções des classes disponíveis

Como você pode ver na tabela abaixo temos uma série de opções disponíveis no LaTeX.

E você pode escolher mais de uma opção pra uma mesma classe. Desde que as separe por vírgulas, como você vai ver no exemplo mais à adiante.

| Tamanho da letra                | Define o tamanho da fonte principal do documento que podem ser 10pt, 11pt e 12pt. Se nenhuma opção for especificada, 10pt será assumido.                                                                                                                                  |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Tamanho da folha                | Define o tamanho do papel. O tamanho padrão é papel de carta (letterpaper). Podem ser especificados os tamanhos a4paper, a5paper, letterpaper, b5paper, executivepaper ou legalpaper.                                                                                     |
| Alinhamento da equação          | O parâmetro opcional fleqn alinha a equação ao lado esquerdo invés de centralizar.                                                                                                                                                                                        |
| Posição da numeração da equação | O parâmetro opcional leqno coloca a numeração das fórmulas no lado esquerdo invés do lado direito.                                                                                                                                                                        |
| Página de título                | titlepage especifica que uma nova página deve ser iniciada após o título do documento. A opção notitlepage especifica o oposto.                                                                                                                                           |
| Colunas de texto                | A opção twocolumn diz ao LaTeX para criar um documento de duas colunas invés de uma.                                                                                                                                                                                      |
| Formato de impressão            | A opção oneside diz que o documento final possui conteúdo apenas em um lado da folha, já a opção twoside informa ao LaTeX que o documento final possui conteúdo dos dois lados da folha.                                                                                  |
| Orientação                      | A opção landscape altera a orientação do documento para o modo de paisagem (horizontal)                                                                                                                                                                                   |
| Lado de abertura de capítulos   | O lado em que os capítulos poderão ser abertos podem ser apenas do lado direito openright (padrão para a classe book) ou em qualquer lado openany (padrão para a classe report).                                                                                          |
| Texto fora da área de texto     | Com a opção draft é possível verificar problemas de hifenização e justificação fazendo o LaTeX inserir um pequeno retângulo na margem direita da linha que contem o problema. Também suprime a inclusão de imagens e mostra apenas um quadro onde normalmente ocorreriam. |

## Veja um exemplo prático

Suponha que você quer definir um documento da classe article, com a dimensão<br>de papel A4, tamanho da fonte de 12pt, orientação de paisagem e com duas colunas.

É simples. Basta incluir o seguinte na primeira linha do seu código principal (main):

```TeX
\documentclass[a4paper, 12pt, landscape, twocolumn]{article}
```

<br>
{%- include end_article.html -%}
