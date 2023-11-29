---
layout: post
lang: en
permalink: cs50-python-libraries/
title: "[CS50's - Introduction to Python] Libraries"
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

#### Table of Contents

<ul class="topics">
<li><a href="#emojize">Emojize</a></li>
<li><a href="#frank">Frank, Ian and Glen’s Letters</a></li>
<li><a href="#adieu_adieu">Adieu, Adieu</a></li>
<li><a href="#guessing_game">Guessing Game</a></li>
<li><a href="#little_professor">Little Professor</a></li>
<li><a href="#bitcoin_price_index">Bitcoin Price Index</a></li>
</ul>

<h2 id="emojize">Emojize</h2>

This problem asks to implement a library that takes user's input for an emoji code (<a href="https://www.webfx.com/tools/emoji-cheat-sheet/" target="_blank">alias</a>) and print it as an emoji.

First we need to install the <a href="https://pypi.org/project/emoji/" target="_blank">emoji library</a>. On the command prompt we do:

```
pip install emoji
```

Now we can code:

1. Import the emoji library.
2. Ask for user input.
3. Use the method <a href="https://pypi.org/project/emoji/" target="_blank">emojize</a> to convert alias into emoji.
4. Then print it.

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

This problem asks to use the <a href="http://www.figlet.org/faq.html" target="_blank">Frank, Ian, and Glen’s letters</a> format in program that:

- Expects zero or two command-line arguments:
  - Zero if the user would like to output text in a random font.
  - Two if the user would like to output text in a specific font, in which case the first of the two should be `-f` or `--font`, and the second of the two should be the name of the font.
- Prompts the user for a str of text.
- Outputs that text in the desired font.
- If the user provides two command-line arguments and the first is not -f or --font or the second is not the name of a font, the program should exit via sys.exit with an error message.

First we need to install the <a href="https://pypi.org/project/pyfiglet/0.7/" target="_blank">pyfiglet library</a>. On the command prompt we do:

```
pip install pyfiglet
```

Now we can code:

1. Import the <a href="https://docs.python.org/3/library/sys.html" target="_blank">sys library</a> to take command-line arguments.
1. Import the <a href="https://docs.python.org/pt-br/3/library/random.html" target="_blank">random library</a> to be abble to use the <a href="https://docs.python.org/pt-br/3/library/random.html#random.choice" target="_blank">choice</a> method to choose the font case user do not input the parameter for font.
1. Import the <a href="https://pypi.org/project/pyfiglet/0.7/" target="_blank">Figlet library</a>.
1. The variable `fonts` creates a list of fonts from Figlet library.
1. If there is only one argument the font will be set randonly from list fonts.
1. if there is 3 argumnts we verify if the second argument is different of `-f` or `--font` or if the font name given by user is not in the list of fonts. If any of these cases are true it will exit the program.
1. If everything is false so we will set the font specified by user.
1. The else means for the case user gives more then three arguments, the program will exit with message `Invalid usage`
1. After setting the font we ask for user message and print it formated in a Figlet font.

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

In this problem we will implement a program that prompts the user for names, one per line, until the user inputs control-d. We will assume that the user will input at least one name. Then bid adieu to those names, separating two names with one and, three names with two commas and one and, and names with commas and one and, as in the below:

> Adieu, adieu, to Liesl <br/>
> Adieu, adieu, to Liesl and Friedrich <br/>
> Adieu, adieu, to Liesl, Friedrich, and Louisa <br/>
> Adieu, adieu, to Liesl, Friedrich, Louisa, and Kurt <br/>
> Adieu, adieu, to Liesl, Friedrich, Louisa, Kurt, and Brigitta <br/>
> Adieu, adieu, to Liesl, Friedrich, Louisa, Kurt, Brigitta, and Marta <br/>
> Adieu, adieu, to Liesl, Friedrich, Louisa, Kurt, Brigitta, Marta, and Gretl

First we need to install the <a href="https://pypi.org/project/inflect/" target="_blank">inflect library</a>. On the command prompt we do:

```
pip install inflect
```

Now we can code:

1. First we import the <a href="https://pypi.org/project/inflect/" target="_blank">inflect library</a>. To make it work we also do `p = inflect.engine()`.
1. The array `names` is set to save the names that user inputs.
1. While the user do not press "control + d" the [exception]({{ "cs50-python-exceptions" | relative_url }}) will not be raised and the user will be asked for a name, and it will be included (<a href="https://docs.python.org/3/tutorial/datastructures.html#more-on-lists" target="_blank">append method</a>) on the `names` array.
1. When the user press control-d the exception will be raised and we wil exit the while loop.
1. The names will then be <a href="https://docs.python.org/3/library/stdtypes.html#str.join" target="_blank">joined</a> to the variable list.
1. And finaly list will be printed to user.

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

In this problem we must implement a program that:

- Prompts the user for a level, $n$. If the user does not input a positive integer, the program should prompt again.
- Randomly generates an integer between 1 and $n$, inclusive, using the random module.
- Prompts the user to guess that integer. If the guess is not a positive integer, the program should prompt the user again.
  - If the guess is smaller than that integer, the program should output Too small! and prompt the user again.
  - If the guess is larger than that integer, the program should output Too large! and prompt the user again.
  - If the guess is the same as that integer, the program should output Just right! and exit.

These are the steps to solve this problem:

1. Import the <a href="https://docs.python.org/pt-br/3/library/random.html" target="_blank">random library</a> to be abble to use the <a href="https://docs.python.org/3/library/random.html#random.randint" target="_blank">randint</a> method to choose a number between 1 and the level given by user.
1. While the level is not a integer higher than 0 (zero) the user will be prompted to input a new number.
1. After condition is met (`level` is a integer higher than zero) we exit the while loop and the program will set a random number between 1 and the `level` given by the user.
1. Then the program asks the user to gues the number while the user has not correctly guessed the number he will be asked to input another number.

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

In this problem we will implement a program that:

- Prompts the user for a level, $n$. If the user does not input 1, 2, or 3, the program should prompt again.
- Randomly generates ten (10) math problems formatted as X + Y = , wherein each of X and Y is a non-negative integer with $n$ digits. No need to support operations other than addition (+).
- Prompts the user to solve each of those problems. If an answer is not correct (or not even a number), the program should output EEE and prompt the user again, allowing the user up to three tries in total for that problem. If the user has still not answered correctly after three tries, the program should output the correct answer.
- The program should ultimately output the user's score: the number of correct answers out of 10.

These are the steps to solve this problem:

1. Import the <a href="https://docs.python.org/pt-br/3/library/random.html" target="_blank">random library</a> to be abble to use the <a href="https://docs.python.org/3/library/random.html#random.randint" target="_blank">randint</a> method to generate a random number in the function `generate_integer` according to user's level choice.
1. The function `get_level` keeps asking a lavel for the user while it is not betwen 1 and 3.
1. In the main function we set some variables:
   - the `level` variable to get the user's level choice by calling the `get_level` function.
   - `errors` to count how many times the user gave a wrong answer for the same expression.
   - `totalErrors` to count how many questions user gave the wrong answer.
1. In the for loop we set two variable to give a random number for `x` and `y` accordding to user's level choice by calling the `generate_integer` function.
1. In <a href="https://docs.python.org/3/reference/compound_stmts.html#try" target="_blank">try</a> we ask user tp input the value for a given expression, if user inputs the wrong value we will raise `ValueError`.

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
In this problem we will implement a program that:

- Expects the user to specify as a command-line argument the number of Bitcoins, $n$, that they would like to buy. If that argument cannot be converted to a float, the program should exit via sys.exit with an error message.
- Queries the API for the CoinDesk Bitcoin Price Index at <a href="https://api.coindesk.com/v1/bpi/currentprice.json" target="_blank">https://api.coindesk.com/v1/bpi/currentprice.json</a>, which returns a JSON object, among whose nested keys is the current price of Bitcoin as a float. Be sure to catch any exceptions, as with code like:

```python
import requests

try:
    ...
except requests.RequestException:
    ...
```

- Outputs the current cost of $n$ Bitcoins in USD to four decimal places, using `,` as a thousands separator.

First we need to install the <a href="https://requests.readthedocs.io/en/latest/" target="_blank">requests library</a>. On the command prompt we do:

```
pip install requests
```

These are the steps to solve this problem:

1. Import the <a href="https://requests.readthedocs.io/en/latest/user/quickstart/#json-response-content" target="_blank">json library</a>, the <a href="https://requests.readthedocs.io/en/latest/user/quickstart/#make-a-request" target="_blank">request library</a> and the <a href="https://docs.python.org/3/library/sys.html#sys.argv" target="_blank">sys library</a>.
1. In the `main` function we use the <a href="https://docs.python.org/3/reference/compound_stmts.html#try" target="_blank">try</a> to verify if the number of arguments given by the user is other than 2, otherwise it exits the program with the message `Missing command-line argument`.
1. If the previous statement is false we check if the value in the second position is a float, we do this by calling the `isFloat` function. Its sole purpose is to verify if the value is a float or not. If not it raises a expetion returning `False` and exiting the program with message `Command-line argument is not a number`.
1. If the conditions to trigger the exit the program is not activated we proceed with the request for the value of Bitcoin in USD and printing it to the user.

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

This is all for week four - Libraries, set of problems of <a href="https://www.edx.org/learn/python/harvard-university-cs50-s-introduction-to-programming-with-python?webview=false&campaign=CS50%27s+Introduction+to+Programming+with+Python&source=edx&product_category=course&placement_url=https%3A%2F%2Fwww.edx.org%2Fcs50" target="_blank">CS50's Introduction to Programming with Python</a> course.
