---
layout: post
lang: pt-BR
title: "Como colocar apenas uma parte do arquivo utilizando \\input"
date: 2021-07-30 18:00:00 -0400
description: "Neste artigo você descobre como colocar apenas uma parte do arquivo utilizando \\input."
image: "/assets/LaTeX/thumb/thumb-latex-6.jpg"
category: LaTeX
tags: LaTeX
---

Gerenciar o conteúdo dos seus documentos é essencial quando trabalhamos com projetos grandes no LaTeX, e por isso dividimos em vários arquivos .tex além do arquivo principal.

Para fazer com que esses outros arquivos sejam incorporados no documento final temos como opção o uso do comando `\input`.

Contudo, nem sempre será necessário inserir todo o conteúdo do arquivo importado no nosso arquivo principal.

Serão apresentadas duas formas de inserir apenas uma parte do arquivo, mas para resolver esse problema nenhuma delas utiliza especificamente o comando input.

## Input a partir da numeração da linha

Para fazer a importação de linhas específicas você pode utilizar o código abaixo:

```TeX
\documentclass[12pt, a4paper]{article}
%Codificação TeX
\makeatletter
ewread\pin@file
ewcounter{pinlineno}
ewcommand\pin@accu{}
ewcommand\pin@ext{pintmp}
% inputs #3, selecting only lines #1 to #2 (inclusive)

ewcommand*\partialinput [3] { %
  \IfFileExists{#3}{ %
    \openin\pin@file #3
    % skip lines 1 to #1 (exclusive)
    \setcounter{pinlineno}{1}
    \@whilenum\value{pinlineno}<#1 \do{ %
      \read\pin@file to\pin@line
      \stepcounter{pinlineno}%
    }
    % prepare reading lines #1 to #2 inclusive
    \addtocounter{pinlineno}{-1}
    \let\pin@accu\empty
    \begingroup
    \endlinechar
ewlinechar
    \@whilenum\value{pinlineno}<#2 \do{ %
      % use safe catcodes provided by e-TeX\'s \readline
      \readline\pin@file to\pin@line
      \edef\pin@accu{\pin@accu\pin@line}%
      \stepcounter{pinlineno}%
    }
    \closein\pin@file
    \expandafter\endgroup
    \scantokens\expandafter{\pin@accu}%
  }{ %
    \errmessage{File `#3\' doesn\'t exist!}%
  }%
}
\makeatother
\begin{document}\partialinput{8}{30}{arquivo.tex}\end{document}
```

O comando `\partialinput` possui três parâmetros obrigatórios: a linha inicial, a linha final e qual arquivo será importado.

```TeX
\partialinput{linha inical}{linha final}{arquivo a ser importado}
```

## Input a partir de tags

Uma outra maneira é utilizando tags para marcar a parte que se deseja importar.

Para fazer isso você deve utilizar o pacote `catchfilebetweentags`, e no corpo de texto o comando `\ExecuteMetaData[arquivo]{tag}`.

Em [arquivo] deve ser informado o nome do arquivo que se deseja importar e em {tag} o nome da tag que marca o conteúdo a ser importado.

O formato de uma tag é do tipo `%<*tag>` para abertura e `%<\tag>` para fechar. Em tag você pode colocar qualquer nome que achar preferível.

Considere o arquivo a ser importado como o seguinte código:

```TeX
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean at varius nunc. %<*parte1>
In feugiat, mauris a varius pulvinar, sapien ex blandit nisl, nec vehicula sem libero non dui.Nam id arcu a mi porttitor vulputate eget non purus. Nullam odio dui, gravida in urna eget, tristique efficitur nibh.
%</parte1>Nullam porta erat purus. Donec euismod posuere dictum. Integer eu mattis neque. Vestibulum mollis nisi non hendrerit bibendum. %<*parte2>
Morbi auctor suscipit massa, ut consequat nunc ultricies non. Cras eleifend nulla neque, in molestie enim malesuada in.Vivamus porttitor in nisi nec porttitor. Pellentesque nec lacinia lorem.
%</parte2>Nunc blandit lacus ut felis porttitor commodo. Vestibulum quis mollis eros.
```

Ele possui duas tags, parte1 e parte2. Agora no arquivo principal:

```TeX
\documentclass[12pt, a4paper]{article}
\usepackage{catchfilebetweentags}

\begin{document}
  \ExecuteMetaData[arquivo.tex]{parte1}
  \ExecuteMetaData[arquivo.tex]{parte2}
\end{document}
```

<br>
{%- include end_article.html -%}
