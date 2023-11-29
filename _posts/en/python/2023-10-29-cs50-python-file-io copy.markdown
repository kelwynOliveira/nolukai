---
layout: post
lang: en
permalink: cs50-python-file-i-o/
title: "[CS50's - Introduction to Python] File I/O"
date: 2023-10-29 18:00:00 -0400
description: "In this post I will show how to solve the problems from topic 6 - File I/O of CS50's - Introduction to Python."
image: "/assets/python/cs50p-file-i-o.jpg"
image-alt: ""
category: python
tags:
  - cs50
  - python
# channel-id: UCYUU9jqWR41rkRXBQHBdbtw
---

In this post I will show how to solve the problems from topic 5 - File I/O of CS50's - Introduction to Python course.

#### Table of Contents

<ul class="topics">
<li><a href="#lines-of-code">Lines of Code</a></li>
<li><a href="#pizza_py">Pizza Py</a></li>
<li><a href="#scourgify">Scourgify</a></li>
<li><a href="#cs50-p-shirt">CS50 P-Shirt</a></li>
</ul>

<h2 id="lines-of-code">Lines of Code</h2>

In this problem we are asked to implement a program that expects exactly one command-line argument, the name (or path) of a Python file, and outputs the number of lines of code in that file, excluding comments and blank lines. If the user does not specify exactly one command-line argument, or if the specified file's name does not end in .py, or if the specified file does not exist, the program should instead exit via `sys.exit`.

We must assume that any line that starts with #, optionally preceded by whitespace, is a comment. (A docstring should not be considered a comment.) Assume that any line that only contains whitespace is blank.

To solve this problem I implemented the following program:

- Import the <a href="https://docs.python.org/3/library/sys.html" target="_blank">sys</a> module to be able to handle the parameters given by the user in the command-line.
- To open the file we use the <a href="https://docs.python.org/3/library/functions.html#open" target="_blank">open</a> command.
- Used the method <a href="https://docs.python.org/3/library/functions.html#open" target="_blank">readlines</a> to read every line of the specified file.

```python
import sys

def main():
    commands = len(sys.argv)
    LoC = 0 # To say how many Lines of Code is there

    if commands < 2:
        sys.exit("Too few command-line arguments")
    if commands > 2:
        sys.exit("Too many command-line arguments")

    length = len(sys.argv[1])

    if sys.argv[1].find(".py", (length - 4)) == -1:
        sys.exit("Not a Python file")
    else:
        try:
            with open(sys.argv[1], "r") as file:
                lines = file.readlines()

            for line in lines:
                if isComment(line) == False:
                    LoC += 1

            print(LoC)

        except FileNotFoundError:
            sys.exit("File does not exist")

def isComment(string):
    string = string.strip(" ")
    if string.startswith("#") or string.isspace():
        return True
    else:
        return False

if __name__ == "__main__":
    main()
```

<a href="https://github.com/kelwynOliveira/CS50_Python/tree/main/07-file-I-O/lines" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

<h2 id="pizza_py">Pizza Py</h2>

This problem asks to implement a program that expects exactly one command-line argument, the name (or path) of a CSV file in Pinocchio's format, and outputs a table formatted as ASCII art using tabulate, a package on PyPI at <a href="https://pypi.org/project/tabulate/" target="_blank">pypi.org/project/tabulate</a>. We must format the table using the library's grid format. If the user does not specify exactly one command-line argument, or if the specified file's name does not end in .csv, or if the specified file does not exist, the program should instead exit via sys.exit.

For this problem my solution was:

- Install the tabulate library with `pip install tabulate`.
- Import the <a href="https://docs.python.org/3/library/sys.html" target="_blank">sys</a> module to be able to handle the parameters given by the user in the command-line.
- To open the file we use the <a href="https://docs.python.org/3/library/functions.html#open" target="_blank">open</a> command.
- Import the csv library to use the method <a href="https://docs.python.org/3/library/csv.html#csv.reader" target="_blank">reader</a> to read the file.
- Import <a href="https://pypi.org/project/tabulate/" target="_blank">tabulate</a> to be able to print the csv file content in a table layout.

```python
import sys
import csv
from tabulate import tabulate

def main():
    args_verification(sys.argv, "csv")
    table = []

    try:
        with open(sys.argv[1], newline='') as file:
            csvfile = csv.reader(file)
            for row in csvfile:
                table.append(row)

            header = table[0]
            print(tabulate(table[1:], header, tablefmt="grid"))

    except FileNotFoundError:
        sys.exit("File does not exist")


def args_verification(arguments, file_tipe):
    commands = len(arguments)
    len_file_type = len(file_tipe) + 2

    if commands < 2:
        sys.exit("Too few command-line arguments")
    if commands > 2:
        sys.exit("Too many command-line arguments")

    length = len(arguments[1])

    if sys.argv[1].find(".csv", (length - len_file_type)) == -1:
        sys.exit("Not a CSV file")

if __name__ == "__main__":
    main()
```

<a href="https://github.com/kelwynOliveira/CS50_Python/tree/main/07-file-I-O/pizza" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

<h2 id="scourgify">Scourgify</h2>

In this problem we will implement a program that:

- Expects the user to provide two command-line arguments:
  - the name of an existing CSV file to read as input, whose columns are assumed to be, in order, name and house, and
  - the name of a new CSV to write as output, whose columns should be, in order, first, last, and house.
- Converts that input to that output, splitting each name into a first name and last name. Assume that each student will have both a first name and last name.

If the user does not provide exactly two command-line arguments, or if the first cannot be read, the program should exit via sys.exit with an error message.

A solution for this problem can be:

- Import the <a href="https://docs.python.org/3/library/sys.html" target="_blank">sys</a> module to be able to handle the parameters given by the user in the command-line.
- To open the file we use the <a href="https://docs.python.org/3/library/functions.html#open" target="_blank">open</a> command.
- Import the csv library to use the method <a href="https://docs.python.org/3/library/csv.html#csv.reader" target="_blank">reader</a> to read the file, the method <a href="https://docs.python.org/3/library/csv.html#csv.DictWriter" target="_blank">DictWriter</a> and <a href="https://docs.python.org/3/library/csv.html#csv.csvwriter.writerow" target="_blank">writerow</a> to write in the csv file.

```python
import sys
import csv

def main():
    args_verification(sys.argv)
    table = []

    try:
        with open(sys.argv[1], newline='') as file:
            csvfile = csv.reader(file)
            for row in csvfile:
                table.append(row)

        with open(sys.argv[2], 'w', newline='') as newfile:
            header = ["first", "last", "house"]
            writer = csv.DictWriter(newfile, fieldnames=header)
            writer.writerow({header[0]: header[0], header[1]: header[1], header[2]: header[2]})

            for row in table[1:]:
                last_name, first_name = row[0].split(",")
                first_name = first_name.strip()
                house = row[1]
                writer.writerow({header[0]: first_name, header[1]: last_name, header[2]: house})

    except FileNotFoundError:
        sys.exit(f"Could not read {sys.argv[1]}")

def args_verification(arguments):
    commands = len(arguments)

    if commands < 3:
        sys.exit("Too few command-line arguments")
    if commands > 3:
        sys.exit("Too many command-line arguments")

if __name__ == "__main__":
    main()
```

<a href="https://github.com/kelwynOliveira/CS50_Python/tree/main/07-file-I-O/scourgify" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

<h2 id="cs50-p-shirt">CS50 P-Shirt</h2>

The description for this problem is:

> After finishing CS50 itself, students on campus at Harvard traditionally receive their very own I took CS50 t-shirt. No need to buy one online, but like to try one on virtually?
>
> In a file called shirt.py, implement a program that expects exactly two command-line arguments:
>
> - in sys.argv[1], the name (or path) of a JPEG or PNG to read (i.e., open) as input
> - in sys.argv[2], the name (or path) of a JPEG or PNG to write (i.e., save) as output
>
>   The program should then overlay shirt.png (which has a transparent background) on the input after resizing and cropping the input to be the same size, saving the result as its output.
>
>   Open the input with Image.open, per <a href="pillow.readthedocs.io/en/stable/reference/Image.html#PIL.Image.open" target="_blank">pillow.readthedocs.io/en/stable/reference/Image.html#PIL.Image.open</a>, resize and crop the input with ImageOps.fit, per <a href="pillow.readthedocs.io/en/stable/reference/ImageOps.html#PIL.ImageOps.fit" target="_blank">pillow.readthedocs.io/en/stable/reference/ImageOps.html#PIL.ImageOps.fit</a>, using default values for method, bleed, and centering, overlay the shirt with Image.paste, per <a href="illow.readthedocs.io/en/stable/reference/Image.html#PIL.Image.Image.paste" target="_blank">pillow.readthedocs.io/en/stable/reference/Image.html#PIL.Image.Image.paste</a>, and save the result with Image.save, per <a href="pillow.readthedocs.io/en/stable/reference/Image.html#PIL.Image.Image.save" target="_blank">pillow.readthedocs.io/en/stable/reference/Image.html#PIL.Image.Image.save</a>.
>
>   The program should instead exit via sys.exit:
>
> - if the user does not specify exactly two command-line arguments,
> - if the input’s and output’s names do not end in .jpg, .jpeg, or .png, case-insensitively,
> - if the input’s name does not have the same extension as the output’s name, or
> - if the specified input does not exist.
>
>   Assume that the input will be a photo of someone posing in just the right way, like <a href="https://cs50.harvard.edu/python/2022/psets/6/shirt/#demos" target="_blank">these demos</a>, so that, when they’re resized and cropped, the shirt appears to fit perfectly.
>
>   If you’d like to run your program on a photo of yourself, first drag the photo over to VS Code’s file explorer, into the same folder as shirt.py. No need to submit any photos with your code. But, if you would like, you’re welcome (but not expected) to share a photo of yourself wearing your virtual shirt in any of <a href="https://cs50.harvard.edu/python/communities" target="_blank">CS50’s communities</a>!

A solutin to this can be:

```python
import sys
import os
from PIL import Image
from PIL import ImageOps

def main():
    args_verification(sys.argv)

    try:
        image = Image.open(sys.argv[1])

    except FileNotFoundError:
        sys.exit("Input does not exist")

    shirt = Image.open("shirt.png")
    size = shirt.size

    photo = ImageOps.fit(image, size)
    photo.paste(shirt, shirt)
    photo.save(sys.argv[2], format=None)

def args_verification(arguments):
    formats = [".jpg", ".jpeg", ".png"]
    commands = len(arguments)
    if commands < 3:
        sys.exit("Too few command-line arguments")
    if commands > 3:
        sys.exit("Too many command-line arguments")

    file1 = os.path.splitext(arguments[1].lower())[1]
    file2 = os.path.splitext(arguments[2].lower())[1]

    if isFileValid(file1, formats) == False:
        sys.exit("Invalid input")
    if isFileValid(file2, formats) == False:
        sys.exit("Invalid output")
    if isSameFormat(file1, file2, formats) == False:
        sys.exit("Input and output have different extensions")

def isFileValid(str, arr):
    for format in arr:
        if format == str:
            return True

    return False

def isSameFormat(str1, str2, arr):
    for format in arr:
        if format == str1 and format == str2:
            return True

    return False

if __name__ == "__main__":
    main()
```

<a href="https://github.com/kelwynOliveira/CS50_Python/tree/main/07-file-I-O/shirt" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

This is all for week six - File I/O, set of problems of <a href="https://www.edx.org/learn/python/harvard-university-cs50-s-introduction-to-programming-with-python?webview=false&campaign=CS50%27s+Introduction+to+Programming+with+Python&source=edx&product_category=course&placement_url=https%3A%2F%2Fwww.edx.org%2Fcs50" target="_blank">CS50's Introduction to Programming with Python</a> course.
