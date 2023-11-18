---
layout: post
lang: pt-BR
title: "Como configurar a forma de exibição de resultados na calculadora"
date: 2020-06-19 18:00:00 -0400
description: "Neste artigo você descobre como configurar a forma de exibição de resultados na sua calculadora, como o científico, número específico de decimais ou exibição normal"
image: "/assets/calculadora/thumb/thumb-calculadora-formas-de-apresentacao.png"
category: calculadora científica
tags: calculadora
channel-id: UCYUU9jqWR41rkRXBQHBdbtw
---

Neste artigo vou falar sobre como configurar a forma de exibição de resultados na calculadora.

Provavelmente a sua calculadora já te apresentou resultados com várias casas decimais, mas na hora da prova você não precisava escrever todos os números.

Dos 8 dígitos decimais que apareciam na prova você só escrevia os três primeiros.

Então escrevi este artigo para que você descubra como configurar a calculadora para exibir uma quantidade máxima fixa de dígitos decimais.

Além disso você descobrirá como configurar a forma de exibição de resultados na calculadora para que ela apresente resultados em notação científica.

As instruções aqui apresentadas são para as calculadoras nos modelos da CASIO FX-82MS, FX-83MS, FX-85MS, FX-270MS, FX-300MS e FX-350MS, mas alguns outros modelos não citados podem apresentar semelhanças.

<!-- Youtube Video -->
<div class="yt-video">
<iframe width="560" height="315" src="https://www.youtube.com/embed/uD7ssZfTXTQ?si=FkG6MAHrvmAC5m-_" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>

{%- include subscribe-channel.html -%}

## Número fixo de casas decimais (Modo Fix)

Primeiramente precisamos encontra a tela de configurações, para isso pressionamos a tecla mode três vezes até a seguinte tela aparecer:

![tela de configuração da forma de exibição de resultados na calculadora]({{ "/assets/calculadora/tela-de-configuracao-para-exibicao-de-digitos.jpg" | relative_url }} "tela de configuração da forma de exibição de resultados na calculadora")

A primeira opção nos permite escolher uma quantidade limite de dígitos decimais, para selecionar pressionamos a tecla 1 (um).

Por conseguinte uma nova tela aparece, aqui escolhemos a quantidade máxima de dígitos que queremos como casas decimais.

Esse valor varia de 0 (zero) até 9 (nove) que você pode escolher apenas digitando o valor na calculadora onde:

- 0 (tecla zero) – não exibirá casas decimais na tela de resultados;
- 1 (tecla um) – exibe apenas um dígito decimal;
- 2 (tecla dois) – exibe dois dígitos decimais;

Acho que é suficiente, mas a ideia segue a mesma para as outras teclas de números.

Por exemplo, um resultado como:

![tela da calculadora com resultado de grande quantidade de dígitos decimais]({{ "/assets/calculadora/resultado-de-1-seno-de-31-graus.jpg" | relative_url }} "tela da calculadora com resultado de grande quantidade de dígitos decimais")

Escolhendo uma exibição de 3 dígitos decimais fica:

![tela da calculadora após configurar a exibição de resultado para apenas 3 dígitos decimais]({{ "/assets/calculadora/escolha-de-um-numero-fixo-de-decimais-na-calculadora.jpg" | relative_url }} "tela da calculadora após configurar a exibição de resultado para apenas 3 dígitos decimais")

## Resultado em notação científica (Modo Sci)

Dizer que um resultado está em notação científica significa que ele possui um dígito antes da vírgula que seja um valor entre 1 e 9, os demais números são dispostos como decimais.

Além disso o resultado pode ser apresentado com um fator de $$10 ^ x$$ sendo multiplicado, por exemplo:

- $$1,45 \times 10 ^ 2$$ é a notação científica para o valor 145;
- $$-2,364 \times 10 ^ -1$$ é a notação científica do valor -0,2364;
- $$0,76 \times 10 ^ 4$$ não está em notação científica pois o zero está na frente da vírgula e não um número entre 1 e 9, para estar em notação científica seria $$7,6 \times 10 ^ 3$$.

Sabendo disso vamos configurar a calculadora para o modo de notação científica.

Para isso pressionamos a tecla mode 3 vezes e escolhemos a opção Sci pressionando o botão de valor 2.

Uma nova tela é a presentada, aqui a calculadora deseja saber a quantidade total de dígitos que você deseja exibir na tela de resultados.

Diferente da opção 1 (modo Fix), nesse modo não contamos apenas a quantidade de dígitos que queremos após a vírgula.

Nesse modo é contabilizado o dígito que vem antes da vírgula, portanto:

- 0 (tecla zero)– diz para a calculadora exibir a capacidade máxima de dígitos da tela de resultados (todos os 10 dígitos);
- 1 (tecla um) – exibe apenas o número antes da vírgula;
- 2 (tecla dois) – exibe o digito antes da vírgula e um dígito decimal;
- 3 (tecla três) – exibe o dígito antes da vírgula e dois dígitos decimais.

Acho que é suficiente para exemplificar, mas a lógica é a mesma para as outras opções. Essa função varia de 0 até 9.

Por exemplo, um resultado como:

![tela com resultado de grande quantidade de dígitos decimais - resultado de 76 x log 64]({{ "/assets/calculadora/resultado-de-76-x-log-64.jpg" | relative_url }} "tela com resultado de grande quantidade de dígitos decimais - resultado de 76 x log 64")

Escolhendo a notação científica com exibição de 3 dígitos ao total fica:

![tela com resultado apresentando apenas 3 dígitos - escolha de notação científica na calculadora]({{ "/assets/calculadora/escolha-de-notacao-cientifica-na-calculadora.jpg" | relative_url }} "tela com resultado apresentando apenas 3 dígitos - escolha de notação científica na calculadora")

## Arredondamentos nesses modos

Ao configurar a forma de exibição de resultados na calculadora temos a questão do arredondamento.

O arredondamento que você vê na tela de resultados ao escolher qualquer um desses modos ocorre apenas para a exibição.

Acontece que a calculadora permanece utilizando 12 dígitos internamente para realizar os cálculos. Então mesmo que você veja o resultado com 3 dígitos a calculadora enxerga ele com 12.

O arredondamento para a exibição de resultados é feito de forma que para número inferiores a 4 é realizado para baixo, acima desse valor (a partir de 5) será arredondado para cima.

Então o valor 2,4763 para exibição no modo Fix de 3 (três) dígitos decimais fica 2,476.

Se configurar o modo Fix para exibir 2 (dois) dígitos decimais então fica 2,48.

## Árvore de comando

Abaixo deixo uma imagem da árvore de comandos sobre como configurar a forma de exibição de resultados na calculadora.

![árvore de comandos sobre como configurar a forma de apresentação de resultados na calculadora]({{ "/assets/calculadora/numero-de-digitos.png" | relative_url }} "árvore de comandos sobre como configurar a forma de apresentação de resultados na calculadora")

Gostou e acha que vai ajudar mais alguém? Então compartilhe.

Tem alguma dúvida? Deixa aqui nos comentários ou pode vir falar comigo pelas redes sociais, os links estão no rodapé do site.

{%- include end_article.html -%}
