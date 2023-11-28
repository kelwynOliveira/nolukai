---
layout: post
lang: en
permalink: cs50-python-conditionals/
title: "[CS50's - Introduction to Python] Solving problems from topic - Conditionals"
date: 2023-09-28 18:00:00 -0400
description: "In this post I will show how to solve the problems from topic 1 - Conditionals of CS50's - Introduction to Python."
image: "/assets/python/cs50p-conditionals.jpg"
image-alt: ""
category: python
tags:
  - cs50
  - python
# channel-id: UCYUU9jqWR41rkRXBQHBdbtw
---

In this post I will show how to solve the problems from topic 1 - Conditionals of CS50's - Introduction to Python course.

<ul class="topics">
<li><a href="#deep_thought">Deep thought</a></li>
<li><a href="#home_federal_savings_bank">Home Federal Savings Bank</a></li>
<li><a href="#file_extensions">File Extensions</a></li>
<li><a href="#math_interpreter">Math Interpreter</a></li>
<li><a href="#meal_time">Meal Time</a></li>
</ul>

<h2 id="deep_thought">Deep Thought</h2>

The first problem brings a dialog from the book "The Hitchhiker’s Guide to the Galaxy" of Douglas Adams where Deep thought, a super computer, answers the Ultimate Question of the Life, the Universe and Everything. Its answer for the question is 42 (fourty-two).

The problem requires we implement a program that prompts yes if user inputs 42, forty-two or fourty two (case-insensitively). Otherwise output no.

Here are the steps to solve this problem:

1. First we need to take user's input, so we will use the command `input`. As per <a href="https://docs.python.org/3/library/functions.html#input" target="_blank">documentation</a> the input command in python returns a string. In this case we don't need to convert 42 to integer.
2. The second step is to remove the white space on the prefix and sufix of the input. As per <a href="https://docs.python.org/3/library/stdtypes.html#str.strip" target="_blank">documentation</a> we can use the method `strip` from `str` object.
3. The next step is to take the input striped and turn it into lowercase to make it case-insensitively. As per <a href="https://docs.python.org/3/library/stdtypes.html#string-methods" target="_blank">documentation</a> we can use the method `lower` from `str` object.
4. The last step is to compare input with expected values, if input matches expected values it prompts "Yes", otherwise it outputs "No".

The solution will then be:

```python
answer = input('What is the Answer to the Great Question of Life, the Universe, and Everything? ')
answer = answer.strip()
answer = str.lower(answer)

if answer == '42' or answer == 'forty-two' or answer == 'forty two':
    print('Yes')
else:
    print('No')
```

<a href="https://github.com/kelwynOliveira/CS50_Python/blob/main/02-conditionals/deep/deep.py" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

<h2 id="home_federal_savings_bank">Home Federal Savings Bank</h2>

This problems asks to implement a program that prompts the user for a greeting. If the greeting starts with "hello", output $0. If the greeting starts with an "h" (but not "hello"), output $20. Otherwise, output $100. In our program we must ignore any leading whitespace in the user's greeting, and treat the user's greeting case-insensitively.

Here are the steps to solve this problem:

1. First we need to take user's input, so we will use the command `input`. As per <a href="https://docs.python.org/3/library/functions.html#input" target="_blank">documentation</a> the input command in python returns a string.
2. The second step is to remove the white space on the prefix and sufix of the input. As per <a href="https://docs.python.org/3/library/stdtypes.html#str.strip" target="_blank">documentation</a> we can use the method `strip` from `str` object.
3. The next step is to take the input striped and turn it into lowercase to make it case-insensitively. As per <a href="https://docs.python.org/3/library/stdtypes.html#string-methods" target="_blank">documentation</a> we can use the method `lower` from `str` object.
4. The last step is to compare input with expected values, and prompt the value according to user's greeting start.

The solution will then be:

```python
greetings = input("Greeting: ")
greetings = greetings.strip()
greetings = str.lower(greetings)

if greetings.startswith("hello"):
    print("$0")
elif greetings.startswith("h"):
    print("$20")
else:
    print("$100")
```

<a href="https://github.com/kelwynOliveira/CS50_Python/blob/main/02-conditionals/bank/bank.py" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

<h2 id="file_extensions">File Extensions</h2>

This problem asks to implement a program that prompts the user for a file name and outputs its format.

Here are the steps to solve this problem:

1. First we need to take user's input, so we will use the command `input`. As per <a href="https://docs.python.org/3/library/functions.html#input" target="_blank">documentation</a> the input command in python returns a string.
2. The second step is to remove the white space on the prefix and sufix of the input. As per <a href="https://docs.python.org/3/library/stdtypes.html#str.strip" target="_blank">documentation</a> we can use the method `strip` from `str` object.
3. The next step is to take the input striped and turn it into lowercase to make it case-insensitively. As per <a href="https://docs.python.org/3/library/stdtypes.html#string-methods" target="_blank">documentation</a> we can use the method `lower` from `str` object.
4. The last step is to compare input with the expected values, and outputs the file media type.

```python
file = input("File name: ")
file = file.strip()
file = str.lower(file)

if file.endswith(".gif"):
    print("image/gif")
elif file.endswith(".jpeg") or file.endswith(".jpg"):
    print("image/jpeg")
elif file.endswith(".png"):
    print("image/png")
elif file.endswith(".pdf"):
    print("application/pdf")
elif file.endswith(".txt"):
    print("text/plain")
elif file.endswith(".zip"):
    print("application/zip")
else:
    print("application/octet-stream")
```

<a href="https://github.com/kelwynOliveira/CS50_Python/blob/main/02-conditionals/extensions/extensions.py" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

<h2 id="math_interpreter">Math Interpreter</h2>

For the problem Math Interpreter is asked to implement a program to calculate an expression given by the user.

Here are the steps to solve this problem:

1. First we need to take user's input, so we will use the command `input`. As per <a href="https://docs.python.org/3/library/functions.html#input" target="_blank">documentation</a> the input command in python returns a string.
1. The second step is to split the input into first value - the x, operation signal (+, -, \* or /) - the y, and the second value, the z. As per <a href="https://docs.python.org/3/library/stdtypes.html#str.split" target="_blank">documentation</a> we can use the method `split` from `str` object. The code will split the values when it finds spaces on user's input.
1. The third step is to transform x and z into float type variables. For this we will use the function <a href="https://docs.python.org/3/library/functions.html#float" target="_blank">float</a>.
1. The next step is to compare the value y with operation signals. I choosed to use the `match` function.
1. The last step is to output the result of the expression.

```python
expression = input("Expression: ")

x, y, z = expression.split(" ")
x = float(x)
z = float(z)

match y:
    case "+":
        operation = x + z
    case  "-":
        operation = x - z
    case  "*":
        operation = x * z
    case  "/":
        operation = x / z

print(f"{operation}")
```

<a href="https://github.com/kelwynOliveira/CS50_Python/blob/main/02-conditionals/interpreter/interpreter.py" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

<h2 id="meal_time">Meal Time</h2>
The objective here is to implement a program that prompts the user for a time and outputs whether it's breakfast time, lunch time, or dinner time. If it's not time for a meal, we will output anything. We must assume that the user's input will be formatted in 24-hour time as #:## or ##:##. And assume that each meal's time range is inclusive. For instance, whether it's 7:00, 7:01, 7:59, or 8:00, or anytime in between, it’s time for breakfast.

We re given the code, but there are missing two functions:

1. main: it is the main function of the program.
1. convert: its role will be convert a given value into a float number.

Here are the steps to solve this problem:

1. First we need to take user's input, so we will use the command `input`. As per <a href="https://docs.python.org/3/library/functions.html#input" target="_blank">documentation</a> the input command in python returns a string.
1. I decided to creat a new function just to handle the time format if it is a.m. or p.m. which I called `timeFormat`. In there I use the method (<a href="https://docs.python.org/3/library/stdtypes.html#str.endswith" target="_blank">endswith</a>) from `str` object. This function calls for the convert function and return its value to the main function.
1. In `convert` I used the <a href="https://docs.python.org/3/library/stdtypes.html#str.split" target="_blank">split</a> method to split the hour and minute. The next step is to transform hours and minutes into float type variables. For this I used the function <a href="https://docs.python.org/3/library/functions.html#float" target="_blank">float</a>. And last this function returns the value of hour as a float number.
1. The function main compares the value of time given by user and prints if it is time to breakfast, lunch or dinner, otherwise it just finshes the program without print anything.

```python
def main():
    time = input("What time is it? ")

    # check if it is a.m. or p.m.
    time = timeFormat(time)

    if time >= 7 and time <= 8:
        print("breakfast time")
    if time >= 12 and time <= 13:
        print("lunch time")
    if time >= 18 and time <= 19:
        print("dinner time")

def convert(time):
    hours, minutes = time.split(":")
    hours = float(hours)
    minutes = float(minutes)

    return hours + minutes / 60

def timeFormat(time):
    if time.endswith("p.m.") or time.endswith("a.m."):
        time, format = time.split(" ")

        if format == "p.m.":
            return convert(time) + 12
        else:
            return convert(time)
    else:
        return convert(time)

if __name__ == "__main__":
    main()
```

<a href="https://github.com/kelwynOliveira/CS50_Python/blob/main/02-conditionals/meal/meal.py" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

This is all for week one - Conditionals, set of problems of <a href="https://www.edx.org/learn/python/harvard-university-cs50-s-introduction-to-programming-with-python?webview=false&campaign=CS50%27s+Introduction+to+Programming+with+Python&source=edx&product_category=course&placement_url=https%3A%2F%2Fwww.edx.org%2Fcs50" target="_blank">CS50's Introduction to Programming with Python</a> course.
