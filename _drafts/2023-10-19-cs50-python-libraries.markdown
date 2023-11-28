---
layout: post
lang: en
permalink: cs50-python-libraries/
title: "[CS50's - Introduction to Python] Solving problems from topic - Libraries"
date: 2023-10-19 18:00:00 -0400
description: "In this post I will show how to solve the problems from topic 4 - Libraries of CS50's - Introduction to Python."
image: "/assets/python/cs50p-libraries.jpg"
image-alt: ""
category: python
tags:
  - cs50
  - python
# channel-id: UCYUU9jqWR41rkRXBQHBdbtw
---

In this post I will show how to solve the problems from topic 4 - Libraries of CS50's - Introduction to Python course.

<ul class="topics">
<li><a href="#emojize">Emojize</a></li>
<li><a href="#frank">Frank, Ian and Glen’s Letters</a></li>
<li><a href="#adieu_adieu">Adieu, Adieu</a></li>
<li><a href="#guessing_game">Guessing Game</a></li>
<li><a href="#little_professor">Little Professor</a></li>
<li><a href="#bitcoin_price_index">Bitcoin Price Index</a></li>
</ul>

<h2 id="emojize">Emojize</h2>

```python
import emoji

text = input("Input: ")
text = emoji.emojize(text, language='alias')

print(f"Output: {text}")
```

<a href="https://github.com/kelwynOliveira/CS50_Python/blob/main/05-libraries/emojize/emojize.py" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

<h2 id="frank">Frank, Ian and Glen’s Letters</h2>

```python
import sys
import random
from pyfiglet import Figlet

figlet = Figlet()
fonts = figlet.getFonts()

if len(sys.argv) == 1:
    figlet.setFont(font=random.choice(fonts))

elif len(sys.argv) == 3:
    if sys.argv[1] != "-f" and sys.argv[1] != "--font" or sys.argv[2] not in fonts:
        sys.exit("Invalid usage")
    figlet.setFont(font=sys.argv[2])
else:
    sys.exit("Invalid usage")

text = input("Input: ")
print(figlet.renderText(text))
```

<a href="https://github.com/kelwynOliveira/CS50_Python/blob/main/05-libraries/figlet/figlet.py" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

<h2 id="adieu_adieu">Adieu, Adieu</h2>

```python
import inflect
p = inflect.engine()
names = []

while True:
    try:
        name = input("Name: ")
        names.append(name)

    except EOFError:
        print()
        break

list = p.join(names)
print(f"Adieu, adieu, to {list}")
```

<a href="https://github.com/kelwynOliveira/CS50_Python/blob/main/05-libraries/adieu/adieu.py" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

<h2 id="guessing_game">Guessing Game</h2>

```python
import random

while True:
    try:
        level = int(input("Level: "))
        if level > 0:
            break
    except:
        pass

randomNumber = random.randint(1, level)

while True:
    try:
        guess = int(input("Guess: "))

        if guess < randomNumber:
            print("Too small!")
        elif guess > randomNumber:
            print("Too large!")
        else:
            print("Just right!")
            break
    except:
        pass
```

<a href="https://github.com/kelwynOliveira/CS50_Python/blob/main/04-exceptions/outdated/outdated.py" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

<h2 id="little_professor">Little Professor</h2>

```python
import random

def main():
    level = get_level()
    errors = 0
    totalErrors = 0

    for _ in range(10):
        x = generate_integer(level)
        y = generate_integer(level)

        while True:
            try:
                answer = int(input(f"{x} + {y} = "))

                if answer == (x + y):
                    break
                else:
                    raise ValueError

            except ValueError:
                errors += 1
                if errors < 3:
                    print("EEE")
                    pass
                else:
                    print("EEE")
                    totalErrors += 1
                    print((f"{x} + {y} = {x + y}"))
                    break

    print(f"Score: {10 - totalErrors}")

def get_level():
    while True:
        try:
            level = int(input("Level: "))
            if level >= 1 and level <=3:
                return level
        except:
            pass

def generate_integer(level):

    match level:
        case 1:
            return random.randint(0, 9)
        case 2:
            return random.randint(10, 99)
        case 3:
            return random.randint(100, 999)

if __name__ == "__main__":
    main()
```

<a href="https://github.com/kelwynOliveira/CS50_Python/blob/main/05-libraries/professor/professor.py" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

<h2 id="bitcoin_price_index">Bitcoin Price Index</h2>

```python
import json
import requests
import sys

def main():
    try:
        if len(sys.argv) != 2:
            sys.exit("Missing command-line argument")
        elif isFloat(sys.argv[1]) == False:
            sys.exit("Command-line argument is not a number")

        response = requests.get("https://api.coindesk.com/v1/bpi/currentprice.json")

        jsonResponse = response.json()
        quantity = float(sys.argv[1])
        btcPrice = jsonResponse["bpi"]["USD"]["rate_float"]

        amount = quantity * btcPrice
        print(f"${amount:,.4f}")

    except requests.RequestException:
        pass

def isFloat(string):
    try:
        float(string)
        return True
    except ValueError:
        return False

main()
```

<a href="https://github.com/kelwynOliveira/CS50_Python/blob/main/05-libraries/bitcoin/bitcoin.py" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

This is all for week three - Libraries, set of problems of <a href="https://www.edx.org/learn/python/harvard-university-cs50-s-introduction-to-programming-with-python?webview=false&campaign=CS50%27s+Introduction+to+Programming+with+Python&source=edx&product_category=course&placement_url=https%3A%2F%2Fwww.edx.org%2Fcs50" target="_blank">CS50's Introduction to Programming with Python</a> course.
