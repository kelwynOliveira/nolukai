---
layout: post
lang: en
permalink: cs50-python-loops/
title: "[CS50's - Introduction to Python] Solving problems from topic - Loops"
date: 2023-10-08 18:00:00 -0400
description: "In this post I will show how to solve the problems from topic 2 - Loops of CS50's - Introduction to Python."
image: "/assets/python/cs50p-loops.jpg"
image-alt: ""
category: python
tags:
  - cs50
  - python
# channel-id: UCYUU9jqWR41rkRXBQHBdbtw
---

In this post I will show how to solve the problems from topic 2 - Loops of CS50's - Introduction to Python course.

<ul class="topics">
<li><a href="#camelcase">camelCase</a></li>
<li><a href="#coke_machine">Coke Machine</a></li>
<li><a href="#just_setting_up_my_twttr">Just setting up my twttr</a></li>
<li><a href="#vanity_plates">Vanity Plates</a></li>
<li><a href="#nutrition_facts">Nutrition Facts</a></li>
</ul>

<h2 id="camelcase">camelCase</h2>

The first problem asks to snake_case every camelCased variable name as input from user.

Here are the steps to solve this problem:

1. First we need to take user's input, so we will use the command `input`. As per <a href="https://docs.python.org/3/library/functions.html#input" target="_blank">documentation</a> the input command in python returns a string.
2. The second step is to verify each letter of user's input using the <a href="https://docs.python.org/3/tutorial/controlflow.html#for-statements" target="_blank">for loop</a>. If it is an uppercased letter it will print the underscore. To verify if it is a uppercased letter I used the method (<a href="https://docs.python.org/3/library/stdtypes.html#str.isupper" target="_blank">isupper</a> from `str` class. And it is a uppercased letter it will be printed in lowercase after the underscore using the method <a href="https://docs.python.org/3/library/stdtypes.html#str.lower" target="_blank">lower</a> from `str` class.

The `end=""` parameter in `print` is to not break the line after printing the caracter/phrase.

The solution will then be:

```python
camel = input("camelCase: ")
print("snake_case: ", end="")

for char in camel:
    if char.isupper():
        print("_", end="")
        char = str.lower(char)
    print(char, end="")

print()
```

<a href="https://github.com/kelwynOliveira/CS50_Python/blob/main/03-loops/camel/camel.py" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

<h2 id="coke_machine">Coke Machine</h2>

This problems asks to implement a program that prompts the user to insert a coin, one at a time, each time informing the user of the amount due. Once the user has inputted at least 50 cents, we must output how many cents in change the user is owed. It says to assume that the user will only input integers, and to ignore any integer that isn’t an accepted denomination.

Here are the steps to solve this problem:

1. First I crated a variable called sum and gave it the value 50.
1. I used the value in sum to verify how much is still missing, <a href="https://docs.python.org/3/reference/compound_stmts.html#while" target="_blank">while</a> the value is greater than 0 it will ask for a coin value from user.
1. The values that user the <a href="https://docs.python.org/3/library/functions.html#input" target="_blank">input</a> will be transformed into a integer variable using the <a href="https://docs.python.org/3/library/functions.html#int" target="_blank">int</a> method.
1. If the value matches any value of acceptable for coins (25, 10 or 5) it will be subtracted from the sum variable.
1. When the value for sum is equal to zero we exit the program, but if sum is lower then zero it will returns the amount owed by the user before exiting.

The solution will then be:

```python
sum = 50

while sum > 0:
    print(f"Amount Due: {sum}")
    value = int(input("Insert Coin: "))

    match value:
        case 25:
            sum -= value
        case 10:
            sum -= value
        case 5:
            sum -= value

sum = -1 * sum
print(f"Change Owed: {sum}")
```

<a href="https://github.com/kelwynOliveira/CS50_Python/blob/main/03-loops/coke/coke.py" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

<h2 id="just_setting_up_my_twttr">Just setting up my twttr</h2>

This problem brings that on twitter is common to shorten words by omitting vowels. For this problem we mas implement a program that prints to user the same text he inputs but without the vowels.

The objective here is to remove the caracters A, E, I, O and U from user's input.

For this problem we will use the <a href="https://docs.python.org/3/reference/compound_stmts.html#the-for-statement" target="_blank">for loop</a> to run through every character on user's input and verify if it is a vowel, if its not a vowel it will be printed.

```python
def main():
    text = input("Input: ")

    for char in text:
        if (isVowel(char) != True):
            print(char, end="")

    print()


def isVowel(c):
    c = c.lower()

    for vowel in "aeiou":
        if c == vowel:
               return True

    return False

main()
```

<a href="https://github.com/kelwynOliveira/CS50_Python/blob/main/03-loops/twttr/twttr.py" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

<h2 id="vanity_plates">Vanity Plates</h2>

For the problem Vanity Plates we must implement a program that prompts the user for a vanity plate and then output Valid if meets all of the requirements or Invalid if it does not. We will assume that any letters in the user's input will be uppercase.

Among the requirements for the vanity plate, are:

- "All vanity plates must start with at least two letters."
- "… vanity plates may contain a maximum of 6 characters (letters or numbers) and a minimum of 2 characters."
- "Numbers cannot be used in the middle of a plate; they must come at the end. For example, AAA222 would be an acceptable … vanity plate; AAA22A would not be acceptable. The first number used cannot be a '0'."
- "No periods, spaces, or punctuation marks are allowed."

This problem give us a structure to work with. The function main is already done, only need to work on the `is_valid` function.

1. The function `is_valid` first verifies the length of the string with method <a href="https://docs.python.org/3/library/functions.html#len" target="_blank">len</a> if its less than two or bigger than 6 it is invalid.
1. The second step is to verify if the **first two** characters to see if they are letters, I used the <a href="https://docs.python.org/3/library/functions.html#func-range" target="_blank">range</a> function to set the range for the for loop. To verify if the character is a leeter I used the <a href="https://docs.python.org/3/library/stdtypes.html#str.isalpha" target="_blank">isalpha</a> method.
1. The next for loop verify if there is any punctuation, spaces or periods with the <a href="https://docs.python.org/3/library/stdtypes.html#bytes.isalnum" target="_blank">isalnum</a> method and if there is a letter after a number with <a href="https://docs.python.org/3/library/stdtypes.html#str.isnumeric" target="_blank">isnumeric</a> and <a href="https://docs.python.org/3/library/stdtypes.html#bytes.isalpha" target="_blank">isalpha</a> methods.
1. The <a href="https://docs.python.org/3/reference/compound_stmts.html#the-while-statement" target="_blank">while loop</a> verifies if the first number is the numer zero (0).

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

main()
```

<a href="https://github.com/kelwynOliveira/CS50_Python/blob/main/03-loops/plates/plates.py" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

<h2 id="nutrition_facts">Nutrition Facts</h2>

The objective here is to implement a program that prompts the user for a fruit and output its calories based on the <a href="https://cs50.harvard.edu/python/2022/psets/2/nutrition/Nutrition-Information-for-Raw-Fruits---small-PDF-Poster.pdf" target="_blank">FDA’s poster for fruits</a>.

To solve this I constructed a <a href="https://docs.python.org/3/tutorial/datastructures.html#dictionaries" target="_blank">dictionary</a> reffering to each fruit on the poster to its calories.

To make it case-insensitive I used the method `lower` to turn every character on input into lowercase. Then printed the calories value according to the fruit the user inputs.

```python
fruits = {
    "apple": 130,
    "avocado": 50,
    "banana": 110,
    "cantaloupe": 50,
    "grapefruit": 60,
    "grapes": 90,
    "honeydew melon": 50,
    "kiwifruit": 90,
    "lemon": 15,
    "lime": 20,
    "nectarine": 60,
    "orange": 80,
    "peach": 60,
    "pear": 100,
    "pineapple": 50,
    "plums": 70,
    "strawberries": 50,
    "sweet cherries": 100,
    "tangerine": 50,
    "watermelon": 80,
}

key = str.lower(input("Item: "))
if key in fruits:
    print(fruits[key])
```

<a href="https://github.com/kelwynOliveira/CS50_Python/blob/main/03-loops/nutrition/nutrition.py" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

This is all for week two - Loops, set of problems of <a href="https://www.edx.org/learn/python/harvard-university-cs50-s-introduction-to-programming-with-python?webview=false&campaign=CS50%27s+Introduction+to+Programming+with+Python&source=edx&product_category=course&placement_url=https%3A%2F%2Fwww.edx.org%2Fcs50" target="_blank">CS50's Introduction to Programming with Python</a> course.
