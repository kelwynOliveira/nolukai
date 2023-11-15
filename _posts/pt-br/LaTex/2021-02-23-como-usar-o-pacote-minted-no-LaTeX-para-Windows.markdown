---
layout: post
lang: pt-BR
title: "Como usar o pacote minted no LaTeX para Windows"
date: 2021-02-23 18:00:00 -0400
description: "Neste artigo você descobre como usar o pacote minted no LaTeX para Windows."
image: "/assets/LaTeX/thumb/thumb-latex-6.jpg"
category: LaTeX
tags: LaTeX
---

O pacote minted é muito útil para realizar o destaque de código fonte no seu documento LaTeX, e neste artigo vou explicar como fazer a instalação no seu computador.

## Passo 1 - Instalação do Python

O primeiro passo é fazer a instalação do python no seu computador. Isso porque o pacote minted utiliza a biblioteca de cores no pacote Pygments por meio do python.
Site para baixar o python: <a href="https://www.python.org/downloads/" target="_blank\">https://www.python.org/downloads/</a>

Eu fiz a instalação do Python 3.9.4

Para verificar se você instalou corretamente abra o prompt de comando e execute python --version. Se algum erro ocorrer <a href="https://packaging.python.org/tutorials/installing-packages/#ensure-you-can-run-python-from-the-command-line\" target="_blank">consulte esta página</a>.

## Passo 2 - Criação da pasta Scripts

Vá até a pasta que você instalou o Python e em seguida crie uma nova pasta chamada Scripts.

Geralmente a pasta em que o Python foi instalado é "C:/Python39"

## Passo 3 - Configuração do sistema

Na barra de pesquisa do Windows digite **sistema**. Na janela que abre, no lado esquerdo, pressione em **Configurações avançadas do sistema**.
Uma nova janela é aberta, na guia **Avançado** selecione **Variáveis de Ambiente…**

![Variáveis de Ambiente]({{ "/assets/LaTeX/variaveis-de-ambiente.jpg" | relative_url }} "Variáveis de Ambiente")

Na seção **Variáveis do sistema** encontre **Path**, clique nele e depois em **Editar...**

Na janela que se abre você deve criar dois novos caminhos, um que leva até a pasta Python e outro que leva para a pasta **Python/Scripts**. E em seguida clique em **OK** em todas as janelas que você abrir.

Passo 4 - Instalalão do pip

Primeiro verifique se já existe uma instalação e qual a versão. Abra o prompt de comandos e digite **pip --version**.

Se você receber um erro faça a <a href="https://pip.pypa.io/en/stable/installing/" target="_blank">instalação do pip</a>.

## Passo 5 - Instalação do Pygments

Através do prompt de comandos vá até a pasta Scripts. Digite cd seguido do caminho da pasta e pressione enter.

![Prompt de comando do python scripts]({{ "/assets/LaTeX/prompt-dedcomando-do-python-scripts.jpg" | relative_url }} "Prompt de comando do python scripts")

Agora escreva o comando pip install Pygments e pressione enter. <a href="https://pygments.org/" target="_blank">https://pygments.org/</a>

Ao finalizar a instalação verifique se tudo deu certo escrevendo **pygmentize --version**, ou abra a pasta Scripts e procure por **pygmentize.exe**.

## Passo 6 - Liberação para o minted acessar o pigmentize

Vá até a pasta raiz do Windows (C:\\Windows) e crie um arquivo com o nome **pygmentize.cmd** (pode ser pelo bloco de notas), dentro deste arquivo escreva:

```Shell
@echo off
set PYTHONPATH=C:\Python27
%PYTHONPATH%\python.exe %PYTHONPATH%\Scripts\pygmentize.exe %\*
```

## Passo 7 - Acesso ao shell do compilador LaTeX

Abra o seu editor de código LaTeX e adicione **-shell-escape** na sua lista de comandos no LaTeX, PdfLaTeX, XeLaTeX, LuaLaTeX...

Para o TexStudio abra **Opções &gt; Configurar TexStudio...**
Na barra da lateral esquerda pressione em **Comandos** e adicione:

```Shell
latex.exe -src -interaction=nonstopmode --shell-escape %.tex
pdflatex.exe -synctex=1 -interaction=nonstopmode -shell-escape %.tex
xelatex.exe -synctex=1 -interaction=nonstopmode -shell-escape %.tex
lualatex.exe -synctex=1 -interaction=nonstopmode -shell-escape %.tex
```

![Configuração de acesso ao shell do compilador LaTeX]({{ "/assets/LaTeX/configuracao-de-acesso-ao-shell-do-compilador-LaTeX.jpg" | relative_url }} "Configuração de acesso ao shell do compilador LaTeX")

Isso deve ser o bastante para poder utilizar o minted.
Caso não funcione copie o arquivo pygmentize.exe para a pasta onde o seu arquivo .tex está.

Em alguns casos é bom limpar o cache para que o pacote minted funcione, para isso insira **`\\usepackage[cache=false]{minted}`** no seu arquivo .tex.

{%- include end_article.html -%}
