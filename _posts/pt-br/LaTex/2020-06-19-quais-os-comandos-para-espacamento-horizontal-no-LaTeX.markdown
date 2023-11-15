---
layout: post
lang: pt-BR
title: "Quais os comandos para espaçamento horizontal no LaTeX"
date: 2020-06-19 18:00:00 -0400
description: "Neste artigo você descobre quais os comandos para espaçamento horizontal no LaTeX."
image: "/assets/LaTeX/thumb/thumb-latex-4.jpg"
category: LaTeX
tags: LaTeX
---

Abaixo é apresentada uma lista dos comandos utilizados para inserir espaços horizontais no LaTeX

- `\quad` - insere um espaço da largura do caractere M
- `\,`- insere um espaçamento equivalente a 3/10 `\quad`, é equivalente à `\thinspace` em modo de texto e `\thinmuskip` no modo matempatico
- `\!` - equivalente negativo de `\,` é o mesmo que `\negthinspace`
- `\:` - no modo matemático corresponde a 4/18 `\quad`, é equivalente à `\>` e `\medspace`
- `\;` - no modo matemático é equivalente a 5/18 `\quad`
- `\qquad` - insere o dobro de `\quad`
- `\kern<largura>` - insere um espaço de largura `<largura>` podendo ser negativo (`\mkern<largura>` no modo matemático)
- `\hspace{largura}` - insere um espaço de largura específica
- `\hphantom{caracteres}` - insere um espaço de largura equivalente ao ocupado pelos caracteres dentro das chaves
- `~` - insere um espaço inquebrável (normalmente para ligar uma palavra com a indicação de uma referência)
- `\hfill` - insere um espaço até preencher toda a linha

| $$\Large Comandos$$                     | $$\Large Resultado$$             |
| --------------------------------------- | -------------------------------- |
| $a\, b$                                 | $$a\, b $$                       |
| $a\thinspace b$                         | $$a\thinspace b$$                |
| $a\!b$                                  | $$a\!b$$                         |
| a\negthinspace b                        | $$a\negthinspace b$$             |
| $a\:b$                                  | $$a\:b$$                         |
| $a\>b$                                  | $$a\>b$$                         |
| $a\;b$                                  | $$a\;b$$                         |
| $a\mkern\thinmuskip b$                  | $$a\,b$$ (similar $\,$)          |
| $a\mkern-\thinmuskip b$                 | $$a! b$$ (similar $\!$)          |
| $a\mkern\medmuskip b$                   | $$a\> b$$ (similar $\:$ ou $\>$) |
| $a\mkern-\medmuskip b$                  | $$a\! b$$                        |
| $a\mkern\thickmuskip b$                 | $$a\; b$$ (similar $\;$)         |
| $a\mkern-\thickmuskip b$                | $$a\! b$$                        |
| a\enspace b                             | $$a\enspace b$$                  |
| $a\enspace b$                           | $$a\enspace b$$                  |
| a\quad b                                | $$a\quad b$$                     |
| $a\quad b$                              | $$a\quad b$$                     |
| a\qquad b                               | $$a\qquad b$$                    |
| $a\qquad b$                             | $$a\qquad b$$                    |
| a\hskip 1em b                           | $$a\hskip 1em b$$                |
| $a\hskip 1em b$                         | $$a\hskip 1em b$$                |
| a\kern 1pc b                            | $$a\kern 1pc b$$                 |
| $a\kern 1pc b$                          | $$a\kern 1pc b$$                 |
| $a\mkern 17mu b$                        | $$a\mkern 17mu b$$               |
| a\hspace{35pt}b                         | $$a\hspace{35pt}b$$              |
| $a\hspace{35pt}b$                       | $$a\hspace{35pt}b$$              |
| axyzb                                   | $$axyzb$$                        |
| a\hphantom{xyz}b (ou $\phantom{xyz}$)   | $$a\hphantom{xyz}b$$             |
| $axyzb$                                 | $$axyzb$$                        |
| $a\hphantom{xyz}b$ (ou $\phantom{xyz}$) | $$a\hphantom{xyz}b$$             |
| a b                                     | $$a b$$                          |
| $a b$                                   | $$a b$$                          |
| a\space b                               | $$a\space b$$                    |
| $a\space b$                             | $$a\space b$$                    |
| a\ b                                    | $$a\ b$$                         |
| $a\ b$                                  | $$a\ b$$                         |
| a{ }b                                   | $$a{ }b$$                        |
| $a{ }b$                                 | $$a{ }b$$                        |
| a~b                                     | $$a~b$$                          |
| $a~b$                                   | $$a~b$$                          |
| a\hfill b                               | $$a\hfill b$$                    |
| $a\hfill b$                             | $$a\hfill b$$                    |

{%- include end_article.html -%}
