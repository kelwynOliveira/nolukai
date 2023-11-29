---
layout: post
lang: en
permalink: cs50-python-regular-expressions/
title: "[CS50's - Introduction to Python] Regular Expressions"
date: 2023-11-01 18:00:00 -0400
description: "In this post I will show how to solve the problems from topic 7 - Regular Expressions of CS50's - Introduction to Python."
image: "/assets/python/cs50p-regular-expressions.jpg"
image-alt: ""
category: python
tags:
  - cs50
  - python
# channel-id: UCYUU9jqWR41rkRXBQHBdbtw
---

In this post I will show how to solve the problems from topic 6 - Regular Expressions of CS50's - Introduction to Python course.

#### Table of Contents

<ul class="topics">
<li><a href="#NUMB3RS">NUMB3RS</a></li>
<li><a href="#watch_on_youtube">Watch on YouTube</a></li>
<li><a href="#working">Working 9 to 5</a></li>
<li><a href="#regular-um-expressions">Regular, um, Expressions</a></li>
<li><a href="#response-validation">Response Validation</a></li>
</ul>

<h2 id="NUMB3RS">NUMB3RS</h2>

In this problem we must implement a function called `validate` that expects an IPv4 address as input as a str and then returns True or False, respectively, if that input is a valid IPv4 address or not.

The tructure of numb3rs.py should be as follows, wherein we're welcome to modify main and/or implement other functions as we see fit, but we may not import any other libraries. We're welcome, but not required, to use re and/or sys.

```python
import re
import sys

def main():
    print(validate(input("IPv4 Address: ")))

def validate(ip):
    ...

...

if __name__ == "__main__":
    main()
```

My solution for this problem is:

- Import <a href="https://docs.python.org/3/library/re.html" target="_blank">re library</a> to be able to use the <a href="https://docs.python.org/3/library/re.html#re.search" target="_blank">search</a> and the <a href="https://docs.python.org/3/library/re.html#re.Pattern.groups" target="_blank">groups</a> methods. A good place to test regular expressions before including it in the code is <a href="https://regexr.com/" target="_blank">https://regexr.com/</a>.

```python
import re

def main():
    print(validate(input("IPv4 Address: ")))

def validate(ip):
    if matches := re.search(r"^([0-9]+)\.([0-9]+)\.([0-9]+)\.([0-9]+)$", ip):
        for matche in matches.groups():
            matche = int(matche)
            print(matche)
            if matche < 0 or matche > 255:
                return False
        return True

    return False

if __name__ == "__main__":
    main()
```

After inplementing `numb3rs.py` I implemented `test_numb3rs.py` to [test]({{ "/cs50-python-unit-tests/" | realative_url }}) the `validate` function as requested.

```python
import numb3rs

def test_valid():
    assert numb3rs.validate("127.0.0.1") == True
    assert numb3rs.validate("255.255.255.255") == True

def test_invalid():
    assert numb3rs.validate("1") == False
    assert numb3rs.validate("1.2") == False
    assert numb3rs.validate("1.2.3") == False
    assert numb3rs.validate("1.512.512.512") == False
    assert numb3rs.validate("1.2.512.512") == False
    assert numb3rs.validate("1.2.3.1000") == False
    assert numb3rs.validate("4000.3.2.1") == False
    assert numb3rs.validate("4000.3000.2.1") == False
    assert numb3rs.validate("4000.3000.2000.1") == False
    assert numb3rs.validate("4000.3000.2000.1000") == False
    assert numb3rs.validate("a.b.c.d") == False
    assert numb3rs.validate("cat") == False
```

<a href="https://github.com/kelwynOliveira/CS50_Python/tree/main/08-regular-expressions/numb3rs" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

<h2 id="watch_on_youtube">Watch on YouTube</h2>

The objective in this problem is to implement a function called `parse` that expects a str of HTML as input, and then extracts any YouTube URL that's the value of a src attribute of an iframe element therein, and returns its shorter, shareable `youtu.be` equivalent as a str. Expect that any such URL will be in one of the formats below. We must assume that the value of src will be surrounded by double quotes. And assume that the input will contain no more than one such URL. If the input does not contain any such URL at all, return None.

- http://youtube.com/embed/xvFZjo5PgG0
- https://youtube.com/embed/xvFZjo5PgG0
- https://www.youtube.com/embed/xvFZjo5PgG0

The structure of watch.py must be as follows:

```python
import re
import sys

def main():
    print(parse(input("HTML: ")))

def parse(s):
    ...

...

if __name__ == "__main__":
    main()
```

My solution for this problem was:

- Import <a href="https://docs.python.org/3/library/re.html" target="_blank">re library</a> to be able to use the <a href="https://docs.python.org/3/library/re.html#re.search" target="_blank">search</a> and the <a href="https://docs.python.org/3/library/re.html#re.Pattern.groups" target="_blank">group</a> methods. A good place to test regular expressions before including it in the code is <a href="https://regexr.com/" target="_blank">https://regexr.com/</a>.

```python
import re

def main():
    print(parse(input("HTML: ")))

def parse(s):
    if matches := re.search(r"src=\"(.+?)\"", s):
        if embURL := re.search(r"youtube.com/embed/(.+)", matches.group(1)):
            return f"https://youtu.be/{embURL.group(1)}"

    return "None"

if __name__ == "__main__":
    main()
```

<a href="https://github.com/kelwynOliveira/CS50_Python/blob/main/08-regular-expressions/watch/watch.py" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

<h2 id="working">Working 9 to 5</h2>

In this problem we are asked to implement a function called `convert` that expects a str in either of the 12-hour formats below and returns the corresponding str in 24-hour format (i.e., 9:00 to 17:00). Expect that AM and PM will be capitalized (with no periods therein) and that there will be a space before each. Assume that these times are representative of actual times, not necessarily 9:00 AM and 5:00 PM specifically.

- 9:00 AM to 5:00 PM
- 9 AM to 5 PM

Raise a ValueError instead if the input to convert is not in either of those formats or if either time is invalid (e.g., 12:60 AM, 13:00 PM, etc.). But do not assume that someone's hours will start ante meridiem and end post meridiem; someone might work late and even long hours (e.g., 5:00 PM to 9:00 AM).

The structure for working.py shuld be as follows:

```python
import re
import sys

def main():
    print(convert(input("Hours: ")))

def convert(s):
    ...

...

if __name__ == "__main__":
    main()
```

A solution for this problem can be:

- Import <a href="https://docs.python.org/3/library/re.html" target="_blank">re library</a> to be able to use the <a href="https://docs.python.org/3/library/re.html#re.search" target="_blank">search</a> and the <a href="https://docs.python.org/3/library/re.html#re.Pattern.groups" target="_blank">group</a> methods. A good place to test regular expressions before including it in the code is <a href="https://regexr.com/" target="_blank">https://regexr.com/</a>.

```python
import re

def main():
    print(convert(input("Hours: ")))

def convert(s):
    if matches := re.search(r"^(([0-9][0-2]*):*([0-5][0-9])*) ([A-P]M) to (([0-9][0-2]*):*([0-5][0-9])*) ([A-P]M)$", s):
        first_hour = time(matches.group(2), matches.group(3), matches.group(4))
        second_hour = time(matches.group(6), matches.group(7), matches.group(8))

        return f"{first_hour} to {second_hour}"
    else:
        raise ValueError

def time(hour, minutes, type):
    hour = int(hour)

    if minutes != None:
        minutes = int(minutes)
    else:
        minutes = 0

    if minutes > 59:
        raise ValueError

    if type == "PM" and hour < 12:
        hour += 12
    elif type == "AM" and hour == 12:
        hour = 0

    return f"{hour:02}:{minutes:02}"

if __name__ == "__main__":
    main()
```

The program `test_working.py` [tests]({{ "/cs50-python-unit-tests/" | realative_url }}) the `convert` function as requested.

```python
import pytest
import working

def test_hour_minute():
    assert working.convert("9:00 AM to 5:00 PM") == "09:00 to 17:00"
    assert working.convert("10:30 PM to 8:50 AM") == "22:30 to 08:50"

def test_onlyHour():
    assert working.convert("9 AM to 5 PM") == "09:00 to 17:00"
    assert working.convert("10 PM to 8 AM") == "22:00 to 08:00"

def test_valueError():
    with pytest.raises(ValueError):
        working.convert("9:60 AM to 5:60 PM")
    with pytest.raises(ValueError):
        working.convert("9 AM - 5 PM")
    with pytest.raises(ValueError):
        working.convert("09:00 AM - 17:00 PM")
```

<a href="https://github.com/kelwynOliveira/CS50_Python/tree/main/08-regular-expressions/working" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

<h2 id="regular-um-expressions">Regular, um, Expressions</h2>

In this problem we must implement a function called `count` that expects a line of text as input as a str and returns, as an int, the number of times that "um" appears in that text, case-insensitively, as a word unto itself, not as a substring of some other word. For instance, given text like hello, um, world, the function should return 1. Given text like yummy, though, the function should return 0.

The structure of `um.py` should be as follows:

```python
import re
import sys

def main():
    print(count(input("Text: ")))

def count(s):
    ...

...

if __name__ == "__main__":
    main()
```

My solution for this problem was:

- Import <a href="https://docs.python.org/3/library/re.html" target="_blank">re library</a> to be able to use the <a href="https://docs.python.org/3/library/re.html#re.findall" target="_blank">findall</a> and the <a href="https://docs.python.org/3/library/re.html#re.IGNORECASE" target="_blank">IGNORECASE</a> methods. A good place to test regular expressions before including it in the code is <a href="https://regexr.com/" target="_blank">https://regexr.com/</a>.

```python
import re

def main():
    print(count(input("Text: ")))

def count(s):
    return len(re.findall(r"\b\W*um\W*\b", s, re.IGNORECASE))

if __name__ == "__main__":
    main()
```

To test `count` the following program can be used:

```python
import um

def test_words():
    assert um.count("um") == 1
    assert um.count("UM") == 1
    assert um.count("yummi") == 0
    assert um.count("ALBUM") == 0

def test_phrase():
    assert um.count("Um, thanks for the album.") == 1
    assert um.count("Um? Mum? Is this that album where, um, umm, the clumsy alums play drums?") == 2
    assert um.count("This is so yummi") == 0

def test_expression():
    assert um.count("um?") == 1
    assert um.count("Hum!?") == 0
    assert um.count("Um, thanks, um...") == 2
```

<a href="https://github.com/kelwynOliveira/CS50_Python/tree/main/08-regular-expressions/um" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

<h2 id="response-validation">Response Validation</h2>

This problem asks to implement a program that prompts the user for an email address via input and then prints Valid or Invalid, respectively, if the input is a syntatically valid email address. You may not use re. And do not validate whether the email address’s domain name actually exists.

In this case we can use the libraries <a href="https://pypi.org/project/validator-collection/" target="_blank">validator-collection</a> or <a href="https://github.com/kvesteri/validators" target="_blank">validators</a> from PyPI.

First we need to install one of either libriries:

- validator-collection: `pip install validator-collection`
- validators: `pip install validators`

I decided to use validator, so my solution for this problem is as follows:

```python
import validators

def main():
    print(validation(input("Text: ")))

def validation(s):
    if validators.email(s):
        return "Valid"
    else:
        return "Invalid"

if __name__ == "__main__":
    main()
```

<a href="https://github.com/kelwynOliveira/CS50_Python/blob/main/08-regular-expressions/response/response.py" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

This is all for week seven - Regular Expressions, set of problems of <a href="https://www.edx.org/learn/python/harvard-university-cs50-s-introduction-to-programming-with-python?webview=false&campaign=CS50%27s+Introduction+to+Programming+with+Python&source=edx&product_category=course&placement_url=https%3A%2F%2Fwww.edx.org%2Fcs50" target="_blank">CS50's Introduction to Programming with Python</a> course.
