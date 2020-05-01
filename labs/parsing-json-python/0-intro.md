# Parsing JSON with Python

Learn how to parse JSON text into native Python data and how to work with results. Python takes care of the hard part and you get to reap all the benefits!

## Objectives

The objective of this training is to learn:

* The need for structured data formats.
* How to read-from and write-to files using Python.
* JSON’s lightweight syntax.
* How to use Python’s JSON module to “load” and “dump” data.
* How to access data elements within nested data.

## Prerequisites

**If you are at a DevNet event and using a provided workstation**, you will be ready to go. You will have:

* A development environment with typical tools and applications.
* A local copy of the required sample code repository. Depending on your event, you will be using one of the following repositories:
    - **dnav3-code**
    - **dne-security-code**
    - **dciv2-code**
    - **meraki-code**

**If you are working from your own workstation**, please review the ***"How to setup your own computer"*** link at the top of this page.

You should also have an understanding of these foundational topics:

* The previous labs in the **"Python Fundamentals"** Learning Lab Module:
  - **"A Brief Introduction to Git"**
  - **"Intro to Python - Part 1"**
  - **"Intro to Python - Part 2"**

## Introduction

**Q: Why store and share data in text format?**</br>
_A: What other format are you going to use?_

Working with data within your own code is great (using your language's native syntax and data types), but what about when you need to share data between applications? How are you going to format the data so that the other app will understand it?  You could export data in some binary format, but doing so tends to be very proprietary and difficult to work with.  Using a structured text format provides a few immediate benefits:

### Structured text is

* Human Readable _(some formats more so than others)_
* Easily Transportable _(many methods exist to send/receive text)_
* Machine Parsable _(an app can parse the text to extract the structured data)_

When needing to send data between applications, we could invent our own formats for how we want to structure the data we are sharing as text, but this doesn't scale - everyone wanting to get data from you would have to learn "your format."  **Standardized Data-Interchange Formats** allow us to learn one (_okay, a few_) data formats that we can all use to send data back and forth between applications.

### Benefits of standardized data-interchange formats

* We don't have to invent them when we want to share data.
* We don't have to write the code to parse these formats, others have already done this for us.
* Once you understand their syntax, you (as a human) can read and write them yourself _(it's just text)_.

There are several prominent standardized data-interchange formats in use today, with the following being the most pervasive:

1. [JSON (JavaScript Object Notation)](https://www.json.org/)
2. [XML (eXtensible Markup Language)](https://www.w3.org/XML/)
3. [YAML (YAML Ain't Markup Language)](http://yaml.org/)

In this lab we will learn how to parse and work with JSON data using the Python programming language, but before we dive into JSON we need to learn how to do some basic text IO (input and output).

**Next: Reading and writing files**
