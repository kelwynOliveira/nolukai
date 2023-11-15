---
layout: post
lang: pt-BR
title: "13 tipos de caixas no LaTeX"
date: 2020-07-05 18:00:00 -0400
description: "Neste artigo você descobre 13 tipos de caixas no LaTeX."
image: "/assets/LaTeX/thumb/thumb-latex-6.jpg"
category: LaTeX
tags: LaTeX
---

Podemos classificar os diferentes tipos de caixas no LaTeX em dois grandes grupos. As caixas da área de texto e as caixas do modo matemático.

As caixas são delimitações de onde o seu conteúdo vai ser inserido.

## Caixas da área de texto

Algumas das caixas podem ser geradas no LaTeX com:

1. `\mbox{conteúdo}` - cria uma caixa horizontal com largura do conteúdo inserido entre as chaves.
1. `\makebox[largura][alinhamento]{conteúdo}` - cria uma caixa horizontal para o conteúdo inserido e recebe parâmetros opcionais como a largura da caixa e o alinhamento do conteúdo (l - esquerda/left, c - centro/center, r - direita/right, s - esticado/stretch);
1. `\makebox`(largura,altura)`{conteúdo}` - O conteúdo entre parênteses é opcional e deve ser sem unidade (por padrão é baseado em 1pt);
1. `\raisebox{profundidade}[altura][elevação]{conteúdo}` - desenha uma caixa horizontal com largura do conteúdo. A profundidade é o espaçamento abaixo do texto, também aceita argumentos opcionais entre colchetes como altura da caixa e elevação (quanto o texto deve subir);
1. `\sbox{local}[largura][alinhamento]{conteúdo}` - salva a caixa em local que foi estabelecida antes com `
ewsavebox` e inserido no texto com `\usebox`;
1. `\fbox{conteúdo}` - gera uma caixa horizontal com a largura do conteúdo e desenha linhas ao redor do conteúdo;
1. `\framebox[largura][alinhamento interno]{conteúdo}` - também desenha linhas ao redor do conteúdo. Com alinhamento do texto em l - esquerda/left (padrão), c - centro/center e r - direita/right;
1. `\parbox[alinhamento][altura][alinhamento interno]{largura}{conteúdo}` - cria uma caixa vertical, com argumentos opcionais entre colchetes. O [alinhamento] é em relação à linha de texto que podem ser c - centro (padrão), t - top/top e b - inferior/bottom;
1. `ambiente minipage` - você pode utilizar o ambiente minipage para criar caixas de texto e possui sintaxe semelhante ao `\parbox`.
1. `\hbox{conteúdo}` - cria uma caixa horizontal, pode ser configurado uma largura com `\hbox to largura{conteúdo}`
1. `\vbox{conteúdo}` - cria uma caixa vertical, pode ser configurado uma altura com `\vbox to altura{conteúdo}`

Exemplo para cada uma das caixas:

```TeX
\begin{document}
  \mbox{texto}
  \makebox[40pt][t]{texto}
  \makebox(40,10){texto}
  \raisebox{10pt}[40pt][5pt]{texto}
  \newsavebox{\caixa}
  \savebox{\caixa}[30mm][t]{texto}
  \usebox{\caixa}
  \fbox{texto}
  \framebox[3cm][l]{texto}
  \parbox[t][1in][c]{2cm}{texto}

  \begin{minipage}[t][5em][c]{2cm}
    texto
  \end{minipage}

  \hbox to 5cm{texto}
  \vbox to 50mm{\hbox{texto}}
\end{document}
```

## Caixas do modo matemático

Com o pacote `mathtools` você tem disponível alguns comandos de criação de caixas que seguirão o modo matemático.

1. `\mathmbox{conteúdo}` - cria uma caixa horizontal com largura do conteúdo inserido entre as chaves.
1. `\mathmakebox[largura][alinhamento]{conteúdo}` - cria uma caixa horizontal para o conteúdo inserido e recebe parâmetros opcionais como a largura da caixa e o alinhamento do conteúdo (l - esquerda/left, c - centro/center, r - direita/right, s - esticado/stretch);

```TeX
\documentclass[12pt]{article}
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage[brazil]{babel}
\usepackage{mathtools}
\begin{document}
\[
\mathmbox{\int_a^b f(x) dx}
\]texto

$ \mathmakebox[4cm][c]{\int_a^b f(x) dx} $
\end{document}
```

<br>

{%- include end_article.html -%}
