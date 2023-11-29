---
layout: post
lang: en
permalink: cs50-python-functions-variables/
title: "[CS50's - Introduction to Python] Functions, Variables"
date: 2023-09-25 18:00:00 -0400
description: "In this post I will show how to solve the problems from topic 0 - Functions and Variables of CS50's - Introduction to Python."
image: "/assets/python/cs50p-functions-variables.jpg"
image-alt: ""
category: python
tags:
  - cs50
  - python
# channel-id: UCYUU9jqWR41rkRXBQHBdbtw
---

In this post I show how to solve the problems from topic 0 - Functions and Variables of CS50's - Introduction to Python course.

#### Table of Contents

<ul class="topics">
<li><a href="#indor_voice">Indoor Voice</a></li>
<li><a href="#playback_speed">Playback Speed</a></li>
<li><a href="#making_faces">Making Faces</a></li>
<li><a href="#einstein">Einstein</a></li>
<li><a href="#tip_calculator">Tip Calculator</a></li>
</ul>

<h2 id="indor_voice">Indoor Voice</h2>

The first problem brings that WRITING IN ALL CAPS IS LIKE YELLING so we have to create a program to lowercase all letters that are in caps.

Here are the steps to solve this problem:

1. First we need to take user's input, so we will use the command <a href="https://docs.python.org/3/library/functions.html#input" target="_blank">input</a>. As per documentation the input command in python returns a string.
2. The second step is to take the input and print it in lowercase. For this we can use the method <a href="https://docs.python.org/3/library/stdtypes.html#string-methods" target="_blank">lower</a>.

The solution will then be:

```python
text = input()
print(str.lower(text))
```

<a href="https://github.com/kelwynOliveira/CS50_Python/blob/main/01-functions-variables/indoor/indoor.py" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

<h2 id="playback_speed">Playback Speed</h2>

This problems simulates a slown down speach. The objective here is to replace the space between words with `...` (i.e., three periods).

Here are the steps to solve this problem:

1. First we need to take user's input, so we will use the command <a href="https://docs.python.org/3/library/functions.html#input" target="_blank">input</a>. As per documentation the input command in python returns a string.
2. The second step is to take the input and print it with `...` in place of spaces. For this we can use the method <a href="https://docs.python.org/3/library/stdtypes.html#string-methods" target="_blank">replace</a>.

The solution will then be:

```python
text = input()
print(text.replace(' ', '...'))
```

<a href="https://github.com/kelwynOliveira/CS50_Python/blob/main/01-functions-variables/playback/playback.py" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

<h2 id="making_faces">Making Faces</h2>

This problem brings that before emojis there where emoticons, which are text representations of the writer's mood like the facial expressions `:-D` to show happiness.

The objective here is to replace two emoticons: `:(` per 🙁 and `:)` per 🙂 when user inputs these emoticons.

For this problem we will use the method <a href="https://docs.python.org/3/library/stdtypes.html#string-methods" target="_blank">replace</a>. Since a emoji is just a representation of a caractere we can justa copy and paste it in our code.

The function `main` takes the input from user and print the emojis if they exist on the users input.

The function `convert` takes a str as parameter to replace the chracters with emoticons to emojis.

```python
def main():
    text = input()
    print(convert(text))

def convert(text):
    text = text.replace(':)', '🙂')
    text = text.replace(':(', '🙁')

    return text

main()
```

<a href="https://github.com/kelwynOliveira/CS50_Python/blob/main/01-functions-variables/faces/faces.py" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

<h2 id="einstein">Einstein</h2>

For the problem Einstein is asked to print the value of energy (Joules) after user inputs a value representing the mass (kilograms), assuming that the user will input a interger.

$$ E = m \times c ^ 2 $$

Where c = 300,000,000 m/s

To solve this problem we will use the class <a href="https://docs.python.org/3/library/functions.html#int" target="_blank">int</a> to change the users input from string to an integer number.

After changing the value input to a integer variable we can calculate the energy E.

```python
m = int(input('m: '))
E = m * 300000000**2
print(f'E: {E}')
```

<a href="https://github.com/kelwynOliveira/CS50_Python/blob/main/01-functions-variables/einstein/einstein.py" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

<h2 id="tip_calculator">Tip Calculator</h2>

The objective here is to complete the code given so we have a program that calculates the tip for the waiter that served you.

There are missing two functions:

1. dollars_to_float: we will use the method <a href="https://docs.python.org/3/library/stdtypes.html#str.removeprefix" target="_blank">removeprefix</a> to remove the dollar symbol (\$) and the function <a href="https://docs.python.org/3/library/functions.html#float" target="_blank">float</a> to change the user's input to a float number.
2. percent_to_float: we will use the method <a href="https://docs.python.org/3/library/stdtypes.html#str.removesufix" target="_blank">removesufix</a> to remove the percent symbol (\%) and the function <a href="https://docs.python.org/3/library/functions.html#float" target="_blank">float</a> to change the user's input to a float number.

```python
def main():
    dollars = dollars_to_float(input("How much was the meal? "))
    percent = percent_to_float(input("What percentage would you like to tip? "))
    tip = dollars * percent
    print(f"Leave ${tip:.2f}")

def dollars_to_float(d):
    d = d.removeprefix('$')
    return float(d)

def percent_to_float(p):
    p = p.removesuffix('%')
    return float(p) / 100

main()
```

<a href="https://github.com/kelwynOliveira/CS50_Python/blob/main/01-functions-variables/tip/tip.py" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

This is all for week zero - Functions, Variables, set of problems of <a href="https://www.edx.org/learn/python/harvard-university-cs50-s-introduction-to-programming-with-python?webview=false&campaign=CS50%27s+Introduction+to+Programming+with+Python&source=edx&product_category=course&placement_url=https%3A%2F%2Fwww.edx.org%2Fcs50" target="_blank">CS50's Introduction to Programming with Python</a> course.
