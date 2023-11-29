---
layout: post
lang: en
permalink: cs50-python-unit-tests/
title: "[CS50's - Introduction to Python] Unit Tests"
date: 2023-10-24 18:00:00 -0400
description: "In this post I will show how to solve the problems from topic 5 - Unit Tests of CS50's - Introduction to Python."
image: "/assets/python/cs50p-unit-tests.jpg"
image-alt: ""
category: python
tags:
  - cs50
  - python
# channel-id: UCYUU9jqWR41rkRXBQHBdbtw
---

In this post I will show how to solve the problems from topic 4 - Unit Tests of CS50's - Introduction to Python course.

#### Table of Contents

<ul class="topics">
<li><a href="#testing_my_twttr">Testing my twttr</a></li>
<li><a href="#back_to_the_bank">Back to the Bank</a></li>
<li><a href="#vanity_plate">Re-requesting a Vanity Plate</a></li>
<li><a href="#refueling">Refueling</a></li>
</ul>

<h2 id="testing_my_twttr">Testing my twttr</h2>

In this problem we will reimplement [Setting up my twttr]({{ "/cs50-python-loops/#just_setting_up_my_twttr" | relative_url }}) from Problem Set 2, restructuring our code per the below, wherein shorten expects a str as input and returns that same str but with all vowels (A, E, I, O, and U) omitted, whether inputted in uppercase or lowercase.

```python
def main():
    ...

def shorten(word):
    ...

if __name__ == "__main__":
    main()
```

I reimplemented [Setting up my twttr]({{ "/cs50-python-loops#just_setting_up_my_twttr" | relative_url }}) as follows:

```python
def main():
    text = input("Input: ")
    print(shorten(text))

def shorten(word):
    str = ""
    for char in word:
        if (char.lower() not in "aeiou"):
            str += char

    return str

if __name__ == "__main__":
    main()
```

Now we will implement the test file. It will test the our implementation of the `shorten` function. For this I creted some functions inside `test_twttr` file each of whose names begins with test\_ so that I could execute my tests with:

```
pytest test_twttr.py
```

To use pytest we must intall it:

```
pip install -U pytest
```

The program to test the `shorten` function will be as follows:

The <a href="https://docs.python.org/3/reference/simple_stmts.html/#the-assert-statement" target="_blank">assert</a> is used to compare result between the value result from function and expected value.

```python
import twttr

def main():
    test_twttr()
    test_number()
    test_punctuation()

def test_twttr():
    assert twttr.shorten("twitter") == "twttr"
    assert twttr.shorten("TEXT") == "TXT"
    assert twttr.shorten("LaTeX") == "LTX"

def test_number():
    assert twttr.shorten("123") == "123"

def test_punctuation():
    assert twttr.shorten(",.?") == ",.?"

if __name__ == "__main__":
    main()
```

<a href="https://github.com/kelwynOliveira/CS50_Python/tree/main/06-unit-tests/test_twttr" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

<h2 id="back_to_the_bank">Back to the Bank</h2>

In this problem we will reimplement [Home Federal Savings Bank]({{ "/cs50-python-conditionals#home_federal_savings_bank" | relative_url }}) restructuring this code per the below, wherein `value` expects a str as input and returns an int, namely 0 if that str starts with "hello", 20 if that str starts with an "h" (but not "hello"), or 100 otherwise, treating the str case-insensitively. We can assume that the string passed to the value function will not contain any leading spaces. Only main should call print.

```python
def main():
    ...

def value(greeting):
    ...

if __name__ == "__main__":
    main()
```

In this case I reimplemented [Home Federal Savings Bank]({{ "/cs50-python-conditionals/#home_federal_savings_bank" | relative_url }}) as per the bellow:

```python
def main():
    greetings = input("Greeting: ")
    print(f"${value(greetings)}")

def value(greeting):
    greeting = greeting.strip()
    greeting = str.lower(greeting)

    if greeting.startswith("hello"):
        return 0
    elif greeting.startswith("h"):
        return 20
    else:
        return 100

if __name__ == "__main__":
    main()
```

Now we create a test file to test the `value` function:

To use pytest we must intall it:

```
pip install -U pytest
```

- test_hello: Testes the word "hello" to be case-insensitive.
- test_h: testes words that starts with "h".
- test_others: tests words that starts with other character than "h".

The <a href="https://docs.python.org/3/reference/simple_stmts.html#the-assert-statement" target="_blank">assert</a> is used to compare result between the value result from function and expected value.

```python
import bank

def main():
    test_hello()
    test_h()
    test_others()


def test_hello():
    assert bank.value("hello") == 0
    assert bank.value("Hello") == 0
    assert bank.value("HELLO") == 0

def test_h():
    assert bank.value("hi") == 20
    assert bank.value("How are you") == 20
    assert bank.value("H") == 20
    assert bank.value("h") == 20

def test_others():
    assert bank.value("Whats your name?") == 100
    assert bank.value("Just saying hi") == 100


if __name__ == "__main__":
    main()
```

<a href="https://github.com/kelwynOliveira/CS50_Python/tree/main/06-unit-tests/test_bank" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

<h2 id="vanity_plate">Re-requesting a Vanity Plate</h2>
This problem asks to reimplement [Vanity Plates]({{ "/cs50-python-cs50-python-loops/#vanity_plates" | relative_url }}) restructuring our code per the below, wherein `is_valid` still expects a str as input and returns True if that str meets all requirements and False if it does not, but main is only called if the value of `__name__` is `"__main__"`:

```python
def main():
    ...

def is_valid(s):
    ...

if __name__ == "__main__":
    main()
```

My reimplementation of [Vanity Plates]({{ "/cs50-python-cs50-python-loops/#vanity_plates" | relative_url }}) is as follows:

```python
def main():
    plate = input("Plate: ")
    if is_valid(plate):
        print("Valid")
    else:
        print("Invalid")


def is_valid(s):
    size = len(s)

    if size < 2 or size > 6:
        return False

    for i in range(2):
        if (s[i].isalpha() != True):
            return False

    for i in range(size):
        if i < size - 1:
            j = i + 1

        if s[i].isalnum() != True:
            return False

        # Verify if after the number has a letter
        if s[i].isnumeric() and s[j].isalpha():
            return False

    # Verify if the first number is zero
    count = 1
    while s[count].isnumeric() != True and count < size - 1:
        if s[count + 1] == '0':
            return False
        count += 1

    return True

if __name__ == "__main__":
    main()
```

The program that tests the function `is_valid` will then be:

The <a href="https://docs.python.org/3/reference/simple_stmts.html#the-assert-statement" target="_blank">assert</a> is used to compare result between the value result from function and expected value.

```python
import plates

def test_valid():
    assert plates.is_valid("CS50") == True

def test_starts_with_0():
    assert plates.is_valid("CS05") == False

def test_number_in_middle():
    assert plates.is_valid("CS50P") == False

def test_puctuation():
    assert plates.is_valid("PI3.14") == False

def test_one_letter():
    assert plates.is_valid("H") == False

def test_more_than_six_digits():
    assert plates.is_valid("OUTATIME") == False

def test_two_first_not_letter():
    assert plates.is_valid("1CS5") == False
    assert plates.is_valid("C123") == False
    assert plates.is_valid("1234") == False
```

<a href="https://github.com/kelwynOliveira/CS50_Python/tree/main/06-unit-tests/test_plates" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

<h2 id="refueling">Refueling</h2>

In this project we must reimplement [Fuel Gauge]({{ "/cs50-python-exceptions/#fuel_auge" | relative_url }}) from Problem Set 3, restructuring our code per the below, wherein:

- `convert` expects a str in X/Y format as input, wherein each of X and Y is an integer, and returns that fraction as a percentage rounded to the nearest int between 0 and 100, inclusive. If X and/or Y is not an integer, or if X is greater than Y, then `convert` should raise a `ValueError`. If Y is 0, then convert should raise a `ZeroDivisionError`.
- `gauge` expects an int and returns a str that is:
  - "E" if that int is less than or equal to 1,
  - "F" if that int is greater than or equal to 99,
  - and "Z%" otherwise, wherein Z is that same int.

```python
def main():
    ...

def convert(fraction):
    ...

def gauge(percentage):
    ...

if __name__ == "__main__":
    main()
```

My reimplementation for this is:

```python
def main():
    while True:
        try:
            n = input("Fraction: ")
            fuel = convert(n)
        except (ValueError, ZeroDivisionError):
            pass
        else:
            break

    print(gauge(fuel))

def convert(fraction):
    numerator, denominator = fraction.split('/')
    numerator = int(numerator)
    denominator = int(denominator)

    if denominator == 0:
        raise ZeroDivisionError

    percentage = round(numerator / denominator * 100)

    if percentage < 0 or percentage > 100:
        raise ValueError
    else:
        return percentage

def gauge(percentage):
    if percentage <= 1:
        return "E"
    elif percentage >= 99:
        return "F"
    else:
        return f"{percentage}%"

if __name__ == "__main__":
    main()
```

The program that tests the function `convert` and `gauge` will then be:

We import pytest to use the method <a href="https://docs.pytest.org/en/7.1.x/getting-started.html#assert-that-a-certain-exception-is-raised" target="_blank">raises</a> to raise the errors.

```python
import fuel
import pytest

def test_convert():
    assert fuel.convert("3/4") == 75
    assert fuel.convert("1/4") == 25
    assert fuel.convert("4/4") == 100
    assert fuel.convert("0/4") == 0

def test_errors():
    with pytest.raises(ZeroDivisionError):
        fuel.convert("4/0")
    with pytest.raises(ValueError):
        fuel.convert("three/four")
    with pytest.raises(ValueError):
        fuel.convert("1.5/3")

def test_gauge():
    assert fuel.gauge(75) == "75%"
    assert fuel.gauge(33) == "33%"
    assert fuel.gauge(0) == "E"
    assert fuel.gauge(1) == "E"
    assert fuel.gauge(99) == "F"
    assert fuel.gauge(100) == "F"
```

The <a href="https://docs.python.org/3/reference/simple_stmts.html#the-assert-statement" target="_blank">assert</a> is used to compare result between the value result from function and expected value.

<a href="https://github.com/kelwynOliveira/CS50_Python/tree/main/06-unit-tests/test_fuel" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

This is all for week five - Unit Tests, set of problems of <a href="https://www.edx.org/learn/python/harvard-university-cs50-s-introduction-to-programming-with-python?webview=false&campaign=CS50%27s+Introduction+to+Programming+with+Python&source=edx&product_category=course&placement_url=https%3A%2F%2Fwww.edx.org%2Fcs50" target="_blank">CS50's Introduction to Programming with Python</a> course.
