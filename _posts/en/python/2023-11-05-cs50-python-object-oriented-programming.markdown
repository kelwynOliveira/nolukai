---
layout: post
lang: en
permalink: cs50-python-object-oriented-programming/
title: "[CS50's - Introduction to Python] Object-Oriented Programming"
date: 2023-11-05 18:00:00 -0400
description: "In this post I will show how to solve the problems from topic 8 - Object-Oriented Programming of CS50's - Introduction to Python."
image: "/assets/python/cs50p-object-oriented-programming.jpg"
image-alt: ""
category: python
tags:
  - cs50
  - python
# channel-id: UCYUU9jqWR41rkRXBQHBdbtw
---

In this post I will show how to solve the problems from topic 7 - Object-Oriented Programming of CS50's - Introduction to Python course.

#### Table of Contents

<ul class="topics">
<li><a href="#seasons_of_love">Seasons of Love</a></li>
<li><a href="#cookie_jar">Cookie Jar</a></li>
<li><a href="#cs50_shirtificate">CS50 Shirtificate</a></li>
</ul>

<h2 id="seasons_of_love">Seasons of Love</h2>

In this problem we will implement a program that prompts the user for their date of birth in YYYY-MM-DD format and then prints how old they are in minutes, rounded to the nearest integer, using English words instead of numerals, just like the song from <a href="https://www.youtube.com/watch?v=xRROQYHkH9U&t=1s" target="_blank">Rent</a>, without any and between words. Since a user might not know the time at which they were born, assume, for simplicity, that the user was born at midnight (i.e., 00:00:00) on that date. And assume that the current time is also midnight. In other words, even if the user runs the program at noon, assume that it's actually midnight, on the same date. Use datetime.date.today to get today's date, per <a href="https://docs.python.org/3/library/datetime.html#datetime.date.today" target="_blank">docs.python.org/3/library/datetime.html#datetime.date.today</a>.

The structure of the program should be as per the below:

```python
from datetime import date

def main():
    ...

...

if __name__ == "__main__":
    main()
```

A solution for this problem can be:

- Import <a href="https://docs.python.org/3/library/datetime.html" target="_blank">datetime</a> to use the methods <a href="https://docs.python.org/3/library/datetime.html#datetime.date" target="_blank">date</a> and <a href="https://docs.python.org/3/library/datetime.html#datetime.date.today" target="_blank">today</a>.
- Import <a href="https://docs.python.org/3/library/re.htm" target="_blank">re</a> to use the methods <a href="https://docs.python.org/3/library/re.html#re.search" target="_blank">search</a> and <a href="https://docs.python.org/3/library/re.html#re.Match.group" target="_blank">group</a>. I used a regular expression to search and separate the day, month and the birth year, function `check_birthday`.
- Import the <a href="https://docs.python.org/3/library/sys.html" target="_blank">sys module</a> to be able to use the method <a href="https://docs.python.org/3/library/sys.html#sys.exit" target="_blank">exit</a> to exit the program user inputss a invalide date.
- Import the <a href="https://pypi.org/project/inflect/" target="_blank">inflect library</a>. To make it work we also do `p = inflect.engine()`. With the method `number_to_words` we can transform numbers into words and print it to the user.

```python
from datetime import date
import re
import sys
import inflect

p = inflect.engine()

def main():
    birth_date = input("Date of Birth: ")
    try:
        year, month, day = check_birthday(birth_date)
    except:
        sys.exit("Invalide Date")

    date_of_birth = date(year, month, day)
    today = date.today()

    count_days = (today - date_of_birth).days
    count_minutes = count_days * 24 * 60
    text_minutes = p.number_to_words(count_minutes, andword="")

    print(f"{text_minutes.capitalize()} minutes")

def check_birthday(date):
    if date := re.search(r"^([0-9]{4})-([0-9]{2})-([0-9]{2})$", date):
        year = int(date.group(1))
        month = int(date.group(2))
        day = int(date.group(3))
        return year, month, day

if __name__ == "__main__":
    main()
```

To test the `check_birthday` function I implemented the folowing test program:

```python
import seasons

def test_date():
    assert seasons.check_birthday("1999-01-01") == (1999, 1, 1)
    assert seasons.check_birthday("1999-1-1") == None
    assert seasons.check_birthday("Jan 1, 1999") == None
```

<a href="https://github.com/kelwynOliveira/CS50_Python/tree/main/09-oop/seasons" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

<h2 id="cookie_jar">Cookie Jar</h2>

The description for this problem is given as bellow:

> Suppose that you’d like to implement a cookie jar in which to store cookies. In a file called jar.py, implement a class called Jar with these methods:
>
> - **init** should initialize a cookie jar with the given capacity, which represents the maximum number of cookies that can fit in the cookie jar. If capacity is not a non-negative int, though, `__init__` should instead raise a ValueError.
> - **str** should return a str with $n$ 🍪, where $n$ is the number of cookies in the cookie jar. For instance, if there are 3 cookies in the cookie jar, then str should return "🍪🍪🍪"
> - deposit should add $n$ cookies to the cookie jar. If adding that many would exceed the cookie jar's capacity, though, `deposit` should instead raise a `ValueError`.
>   `withdraw` should remove $n$ cookies from the cookie jar. Nom nom nom. If there aren't that many cookies in the cookie jar, though, `withdraw` should instead raise a `ValueError`.
>   `capacity` should return the cookie jar's capacity.
>   `size` should return the number of cookies actually in the cookie jar, initially 0.
>
> Structure your class per the below. You may not alter these methods’ parameters, but you may add your own methods.

```python
class Jar:
    def __init__(self, capacity = 12):
        ...

    def __str__(self):
        ...

    def deposit(self, n):
        ...

    def withdraw(self, n):
        ...

    @property
    def capacity(self):
        ...

    @property
    def size(self):
        ...
```

A solution for this can be:

```python
# capacity is the cookie jar's capacity
# size is the number of cookies actually in the cookie jar

class Jar:
    def __init__(self, capacity = 12):
        if capacity < 0:
            raise ValueError("Capacity must be over 0")
        self._capacity = capacity
        self._size = 0

    def __str__(self):
        return "🍪" * self.size

    def deposit(self, n):
        total = self.size + n
        if total > self.capacity:
            raise ValueError(f"Cannot deposity this value of cookies. You can add to {self.capacity - self.size} cookies")
        else:
            self._size = total

    def withdraw(self, n):
        total = self.size - n
        if total < 0:
            raise ValueError(f"Cannot remove this value of cookies. You can remove up to {self.size} cookies")
        else:
            self._size = total

    @property
    def capacity(self):
        return self._capacity

    @property
    def size(self):
        return self._size

def main():
    myJar = Jar()
    myJar.deposit(2)
    myJar.withdraw(1)
    print(myJar)

if __name__ == "__main__":
    main()
```

To test this program we can use:

- About tests see [unit test post]({{ "/cs50-python-unit-tests/" | relative_url }})

```python
from jar import Jar
import pytest

def test_init():
    jar = Jar()
    assert jar.capacity == 12
    jar2 = Jar(4)
    assert jar2.capacity == 4
    with pytest.raises(ValueError):
        jar3 = Jar(-4)

def test_str():
    jar = Jar()
    assert str(jar) == ""
    jar.deposit(1)
    assert str(jar) == "🍪"
    jar.deposit(11)
    assert str(jar) == "🍪🍪🍪🍪🍪🍪🍪🍪🍪🍪🍪🍪"

def test_deposit():
    jar = Jar()
    jar.deposit(4)
    assert jar.size == 4
    jar.deposit(3)
    assert jar.size == 7
    with pytest.raises(ValueError):
        jar.deposit(6)

def test_withdraw():
    jar = Jar()
    jar.deposit(8)
    jar.withdraw(4)
    assert jar.size == 4
    jar.withdraw(3)
    assert jar.size == 1
    with pytest.raises(ValueError):
        jar.withdraw(3)
```

<a href="https://github.com/kelwynOliveira/CS50_Python/tree/main/09-oop/jar" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

<h2 id="cs50_shirtificate">CS50 Shirtificate</h2>

In this problem we are asked to implement a program that prompts the user for their name and outputs, using <a href="https://pypi.org/project/fpdf2/" target="_blank">fpdf2</a>, a CS50 shirtificate in a file called shirtificate.pdf, with these specifications:

- The orientation of the PDF should be Portrait.
- The format of the PDF should be A4, which is 210mm wide by 297mm tall.
- The top of the PDF should say “CS50 Shirtificate” as text, centered horizontally.
- The shirt’s image should be centered horizontally.
- The user’s name should be on top of the shirt, in white text.

A solution for this problem can be:

To use <a href="https://pypi.org/project/fpdf2/" target="_blank">fpdf2</a> we must install it:

```
pip install fpdf2
```

```python
from fpdf import FPDF

class PDF(FPDF):
    def __init__(self, name):
        self._pdf = FPDF()
        self._pdf.add_page()
        self.header()
        self.shirt()
        self.content(name)

    def header(self):
        self._pdf.set_font("helvetica", "B", 16)
        self._pdf.cell(0, 60, "CS50 Shirtificate", new_x="LMARGIN", new_y="NEXT", align='C')

    def shirt(self):
        self._pdf.image("shirtificate.png", w=self._pdf.epw)

    def content(self, name):
        self._pdf.set_font_size(30)
        self._pdf.set_text_color(255,255,255)
        self._pdf.text(60, 140, text=f"{name} took CS50")

    def save(self, name):
        self._pdf.output(name)

def main():
    name = input("Name: ")
    pdf = PDF(name)
    pdf.save("shirtificate.pdf")

if __name__ == "__main__":
    main()
```

<a href="https://github.com/kelwynOliveira/CS50_Python/tree/main/09-oop/shirtificate" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

This is all for week eight - Object-Oriented Programming, set of problems of <a href="https://www.edx.org/learn/python/harvard-university-cs50-s-introduction-to-programming-with-python?webview=false&campaign=CS50%27s+Introduction+to+Programming+with+Python&source=edx&product_category=course&placement_url=https%3A%2F%2Fwww.edx.org%2Fcs50" target="_blank">CS50's Introduction to Programming with Python</a> course.
