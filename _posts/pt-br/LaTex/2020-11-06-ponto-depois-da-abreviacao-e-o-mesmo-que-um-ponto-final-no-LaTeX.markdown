---
layout: post
lang: pt-BR
title: "Ponto depois da abreviação é o mesmo que um ponto final no LaTeX"
date: 2020-11-06 18:00:00 -0400
description: "Neste artigo você descobre sobre porque o ponto depois da abreviação não é o mesmo que um ponto final no LaTeX."
image: "/assets/LaTeX/thumb/thumb-latex-4.jpg"
category: LaTeX
tags: LaTeX
---

Existe sim uma diferença entre o que o LaTeX considera um ponto final e um ponto de abreviação.

Isso está relacionado ao espaçamento que o LaTeX dá considerando essas duas situações.

O espaçamento de uma abreviação é bem menor que o espaçamento gerado por um ponto final.

Quando existe um ponto depois de uma letra em maiúsculo o LaTeX considera que é uma abreviação.

Isso é bem conveniente, mas não quer dizer que vai se aplicar a todo os nossos casos.

Por exemplo, o LaTeX vai considerar o espaço de abreviação quando colocarmos um ponto final depois de uma sigla, o que não deve acontecer.

Para os casos de abreviações em letra minúsculas insira a `\` (contra barra) depois do ponto da abreviação.

Quando for uma sigla, antes do ponto final insira `\@`.

```TeX
\begin{document}
  \noindent
  Harry Potter foi escrito por J. K. Rowling. Ela é bem famosa.\\
  O espaço de etc. é diferente quando se tem por exemplo ABNT. Não é?\\
  O espaço de etc.\ é diferente quando se tem por exemplo ABNT\@. Não é?
\end{document}
```

![Abreviação no LaTeX]({{ "/assets/LaTeX/abreviacao-no-LaTeX.jpg" | relative_url }} "Abreviação no LaTeX")

Para evitar essa automação de espaçamento e considerar todos os espaços as mesmas distâncias, independente de ser uma abreviação ou um ponto final, insira no preâmbulo o comando **\frenchspacing**.

{%- include end_article.html -%}
