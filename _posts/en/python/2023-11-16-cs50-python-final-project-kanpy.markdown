---
layout: post
lang: en
permalink: cs50-python-final-project-kanpy/
title: "[CS50's - Introduction to Python] Final Project - Kanpy"
date: 2023-11-16 18:00:00 -0400
description: "In this post I will show my Final Project called Kanpy for CS50's - Introduction to Python."
image: "/assets/python/cs50-python-final-project-kanpy.jpg"
image-alt: ""
category: python
tags:
  - cs50
  - python
channel-id: UCYUU9jqWR41rkRXBQHBdbtw
---

This project is a command-line interface Kanban board created using Python for <a href="https://www.edx.org/learn/python/harvard-university-cs50-s-introduction-to-programming-with-python?webview=false&campaign=CS50%27s+Introduction+to+Programming+with+Python&source=edx&product_category=course&placement_url=https%3A%2F%2Fwww.edx.org%2Fcs50" target="_blank">CS50's Introduction to Programming with Python</a> course final project.

<!-- Youtube Video -->
<div class="yt-video">
<iframe width="560" height="315" src="https://www.youtube.com/embed/V7HFOg4AgD0?si=WaP1oDTF6rM4-Z0O" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</div>

{%- include subscribe-channel.html -%}

## What a Kanban is?

The Japanese word kanban means "visual board", "sign" or "card" and could be used to refer to a signalling system that uses cards.

Various methodologies and frameworks used in agility, such as Scrum, for example, use a board that we can call a "Kanban board", in which we have some cards that move around the board, in other words, some "kanbans".

In general, the Kanban system has three different phases:

1. **To Do**: represents the tasks or items that have yet to be done. This is the first stage of the process, in which demands are registered and prioritised. This column or section on the Kanban board serves as a reservoir for future activities.

2. **Doing**: in this stage, the tasks previously belonging to the "To Do" column are moved to the "Doing" column and assigned to team members. Work is then started and progresses to completion. This column on the Kanban board shows the tasks that are being worked on and in the process of being carried out.

3. **Done**: when a task is finalised, it is moved to the "Done" column on the Kanban board. The "Done" column serves as a visual indicator of tasks that have been successfully completed.

## About this project

This project is a command-line interface Kanban board created using Python.

It uses a csv file to save the items/activities to be included in the board.

If the file does not exist it will be created. The head of the csv fil is the activity **ID**, the activity **Status** and the activity **Title**.

- **ID** - the number of the activity. It will be useful for selecting the activity and atribute a action for it.
- **Status** - it is the status of the activity according to the kanban board: To Do, Doing or Done
- **Title** - it is the title of the activity.

The following are the ways to interact with the board (case-insensitive):

- **I** - to include a new item/activity to the board. It will be included in last.
- **M** - to move the activity to its status: To Do, Doing or Done.
- **U** - to update the title of the activity.
- **D** - to delete the activity.
- **E** - to close the program.

## Screenshot of the command-line

![Screenshot of the command-line running the Kanthon program. It shows the Kanban board and the actions user can do.](https://raw.githubusercontent.com/kelwynOliveira/CS50_Python/main/final_project/Kanpy.jpg)

## Usage

To use this project you need to instal the folowing libraries:

```python
pip install tabulate
pip install colorama
```

<a href="https://github.com/kelwynOliveira/CS50_Python/tree/main/final_project" target="_blank">
    <svg class="svg-icon">
      <use xlink:href="{{ '/assets/svg/minima-social-icons.svg#github' | relative_url }}"></use>
    </svg>
    <span class="username">GitHub repository</span>
</a>

## Certificate

<img class="thumb" src="https://raw.githubusercontent.com/kelwynOliveira/Assets/main/img/certificates/intensive-courses/cs50/CS50s-introduction-to-programming-with-python.jpg" alt="CS50's introduction to programming with python course certificate">
