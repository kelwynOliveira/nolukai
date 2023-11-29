---
layout: post
lang: en
permalink: cs50-python-exceptions/
title: "[CS50's - Introduction to Python] Exceptions"
date: 2023-10-16 18:00:00 -0400
description: "In this post I will show how to solve the problems from topic 3 - Exceptions of CS50's - Introduction to Python."
image: "/assets/python/cs50p-exceptions.jpg"
image-alt: ""
category: python
tags:
  - cs50
  - python
# channel-id: UCYUU9jqWR41rkRXBQHBdbtw
---

In this post I will show how to solve the problems from topic 3 - Exceptions of CS50's - Introduction to Python course.

#### Table of Contents

<ul class="topics">
<li><a href="#fuel_gauge">Fuel Gauge</a></li>
<li><a href="#felipes_taqueria">Felipe’s Taqueria</a></li>
<li><a href="#grocery_list">Grocery List</a></li>
<li><a href="#outdated">Outdated</a></li>
</ul>

<h2 id="fuel_gauge">Fuel Gauge</h2>

The first problem asks to implement a program that prompts the user for a fraction, formatted as X/Y, where in each of X and Y is an integer, and then outputs, as a percentage rounded to the nearest integer, how much fuel is in the tank. If, though, 1% or less remains, output E instead to indicate that the tank is essentially empty. And if 99% or more remains, output F instead to indicate that the tank is essentially full.

Here are the steps to solve this problem:

1. First we will use the method <a href="https://docs.python.org/3/reference/compound_stmts.html#try" target="_blank">try</a> to calculate a fraction.
1. In the try method I ask for the user to input a fraction and then split it in the '/' character for the numerator and denomitaor values of fraction using the method <a href="https://docs.python.org/3/library/stdtypes.html#str.split" target="_blank">split</a>. Then turn these char numbers into integer values with <a href="https://docs.python.org/3/library/functions.html#int" target="_blank">int</a> function.
1. The fraction result is rounded using the function <a href="https://docs.python.org/3/library/functions.html#round" target="_blank">round</a>.
1. If the value of fuel is lower than zero or gratter then 100 I used the value of fuel to divide it per 0, it will raise a <a href="https://docs.python.org/3/library/exceptions.html#ZeroDivisionError" target="_blank">ZeroDivisionError</a> executing the <a href="https://docs.python.org/3/tutorial/errors.html#handling-exceptions" target="_blank">exception</a> and then the user will be asked for another value again.
1. If the user gives an invalid input or the result for the division is invalid it will raise a <a href="https://docs.python.org/3/tutorial/errors.html#handling-exceptions" target="_blank">ValueError</a> exception asking again the user for a proper input.
1. The `else` `break` command exits the while loop if an exception does not raise.
1. The last ifs conditions verifies the fuel level and prompts the user with the result of fuel.

The solution will then be:

```python
while True:
    try:
        numerator, denominator = input("Fraction: ").split('/')
        numerator = int(numerator)
        denominator = int(denominator)

        fuel = round(numerator / denominator * 100)

        if fuel < 0 or fuel > 100:
            fuel = fuel / 0
    except (ValueError, ZeroDivisionError):
        pass
    else:
        break

if fuel <= 1:
    print("E")
elif fuel >= 99:
    print("F")
else:
    print(f"{fuel}%")
```

<a href="https://github.com/kelwynOliveira/CS50_Python/blob/main/04-exceptions/fuel/fuel.py" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

<h2 id="felipes_taqueria">Felipe's Taqueria</h2>

This problems asks to implement a program that enables a user to place an order, prompting them for items, one per line, until the user inputs control-d (which is a common way of ending one's input to a program). After each inputted item, display the total cost of all items inputted thus far, prefixed with a dollar sign ($) and formatted to two decimal places. We must treat the user's input case insensitively and ignore any input that isn't an item assuming that every item on the menu will be titlecased.

Here are the steps to solve this problem:

1. First I crated a <a href="https://docs.python.org/3/tutorial/datastructures.html#dictionaries" target="_blank">dictionary</a> called menu with all the items.
1. Next I created a variable called total to sum the values of items asked by the customer. It starts with value zero.
1. Then I set a <a href="https://docs.python.org/3/reference/compound_stmts.html#while" target="_blank">while</a> loop to keep asking customer about the products he wants.
1. The method <a href="https://docs.python.org/3/reference/compound_stmts.html#try" target="_blank">try</a> will user for a product. If the item is found on dictionary it will sum its value with the value on total. The method <a href="https://docs.python.org/3/library/stdtypes.html#str.title" target="_blank">title</a> return a titlecased version of the string in this case to match with dictionary keys. The method <a href="https://docs.python.org/3/library/stdtypes.html#str.title" target="_blank">format</a> perform a string formatting operation, in this case to match the format informed on `{:0.2f}`, float number with two decimals.
1. Whe customer press control-d it will raise a <a href="https://docs.python.org/3/library/exceptions.html#EOFError" target="_blank">EOFError</a> and will raise the exception exiting the while loop.

The solution will then be:

```python
menu = {
    "Baja Taco": 4.00,
    "Burrito": 7.50,
    "Bowl": 8.50,
    "Nachos": 11.00,
    "Quesadilla": 8.50,
    "Super Burrito": 8.50,
    "Super Quesadilla": 9.50,
    "Taco": 3.00,
    "Tortilla Salad": 8.00
}

total = 0.00
while True:
    try:
        item = str.title(input("Item: "))

        if item in menu:
            total += menu[item]
            print("Total: ${:0.2f}".format(total))

    except EOFError:
        print()
        break
```

<a href="https://github.com/kelwynOliveira/CS50_Python/blob/main/04-exceptions/taqueria/taqueria.py" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

<h2 id="grocery_list">Grocery List</h2>

This problem asks to implement a program that prompts the user for items, one per line, until the user inputs control-d. Then output the user's grocery list in all uppercase, sorted alphabetically by item, prefixing each line with the number of times the user inputted that item. There is no need to pluralize the items. We must treat the user's input case-insensitively.

Here are the steps I used to solve this problem:

1. I created two <a href="https://docs.python.org/3/tutorial/datastructures.html#dictionaries" target="_blank">dictionaries</a>, one to include the user's list and other to sort it.
1. The <a href="https://docs.python.org/3/reference/compound_stmts.html#while" target="_blank">while</a> loop we keep asking for user's input untill it raises the exception <a href="https://docs.python.org/3/library/exceptions.html#EOFError" target="_blank">EOFError</a> that breaks the loop.
1. On the <a href="https://docs.python.org/3/reference/compound_stmts.html#try" target="_blank">try</a> method we ask for user's input and save it into the `groceries` dictionary, if it already exists we will add a value to the existing number of times the user inserted the item, otherwise it will be created a new key with the value 1.
1. On exception the program <a href="https://docs.python.org/3/library/stdtypes.html#list.sort" target="_blank">sort</a> the groceries dictionary and then give its respective value for times user inserted item. And finaly print the list for the user.

The solution will then be:

```python
groceries = {}
listSorted = {}

while True:
    try:
        item = str.upper(input())

        if item not in groceries:
            groceries[item] = 1
        else:
            groceries[item] += 1

    except EOFError:
        if len(groceries) > 0:
            keys = list(groceries.keys())
            keys.sort()
            for i in keys:
                listSorted[i] = groceries[i]

            for i in listSorted:
                print(f"{listSorted[i]} {i}")

        break
```

<a href="https://github.com/kelwynOliveira/CS50_Python/blob/main/04-exceptions/grocery/grocery.py" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

<h2 id="outdated">Outdated</h2>

This problem brings that in the United States of America the dates are typically formatted in month-day-year order (MM/DD/YYYY) but computers tend to use use <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a> formatted in year-month-day (YYYY-MM-DD). So we must implement a program that asks user for a date in month-day-year order, formatted like 9/8/1636 or September 8, 1636, wherein the month in the latter might be any of the values in the given list.

Here are the steps to solve this problem:

1. Create a <a href="https://docs.python.org/3/tutorial/datastructures.html#dictionaries" target="_blank">dictionary</a> for the months.
1. With the method <a href="https://docs.python.org/3/library/stdtypes.html#bytes.find" target="_blank">find</a> we can check if the user inserted a date with `/` or `,`. In both case we will use the method <a href="https://docs.python.org/3/library/stdtypes.html#str.split" target="_blank">split</a> to split the values for `month`, `day` and `year`.
1. If user inputs a date using `/` the month must be a number, else it should raise an exception and ask user again for a date.
1. If user uses the name of the month it will look into the dictionary for its value in number.
1. If the value of month is not between 1 and 12 or the value for the day is not between 1 and 31, it will rais an exception and ask user for a date again.
1. The else statement for try will break the while loop and then the program will prompt the user for a date in the format of yyy-mm-dd.

The solution will then be:

```python
months = {
    "January": 1,
    "February": 2,
    "March": 3,
    "April": 4,
    "May": 5,
    "June": 6,
    "July": 7,
    "August": 8,
    "September": 9,
    "October": 10,
    "November": 11,
    "December": 12,
}

while True:
    try:
        date = input("Date: ")
        if date.find("/") > -1:
            month, day, year = date.split('/')
            if month in months:
                value = 1 / 0

        elif date.find(",") > -1:
            i, year = date.split(', ')
            month, day = i.split()
            if month in months:
                month = months[month]
            else:
                value = 1 / 0

        else:
            value = 1 / 0

        year = int(year)
        month = int(month)
        day = int(day)

        if month < 1 or month > 12 or day < 1 or day > 31:
            value = 1 / 0

    except ZeroDivisionError:
        pass
    else:
        break

print(f"{year:04}-{month:02}-{day:02}")
```

<a href="https://github.com/kelwynOliveira/CS50_Python/blob/main/04-exceptions/outdated/outdated.py" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

This is all for week three - Exceptions, set of problems of <a href="https://www.edx.org/learn/python/harvard-university-cs50-s-introduction-to-programming-with-python?webview=false&campaign=CS50%27s+Introduction+to+Programming+with+Python&source=edx&product_category=course&placement_url=https%3A%2F%2Fwww.edx.org%2Fcs50" target="_blank">CS50's Introduction to Programming with Python</a> course.
