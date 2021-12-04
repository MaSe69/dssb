---
layout: 20_python
title: Python Before Dataframes
permalink: /Python_before_dataframes
---

# Python - Before Dataframes


## Text output to console
>
    print("Hello, Dataframes in Python")

In Python, Strings are denoted by single or double quotation marks ('text' or "text").
For efficiency with conversion to Julia, here only double quotation marks are used.

>
    language = "Python"
    println("Hello, ", language)


## String Operations

Strings are immutable. Hence, this does not work: 
>
    language[1] = "C"

Common  workaround for immutable Strings: New string composed of parts of old string

In Python, "String concatenation can simply be done with a plus ( + ) sign. 

>
    stringConcat = "Language: "  + language[1:]
    print(stringConcat)


### Numbers

Implicit type definition by representative + Type conversion

>
    n = 5
    x = 7.7
    y = n * x
    print(y)
    myInt = int(y)    ### Conversion is a bit straightforward
    print(myInt)
    print(type(language), type(n), type(y), type(myInt))


### Loops

Python starts with 1
Python needs indent, but does not need an 'end'

>
for i in range(4):
    if i > 1:
        print("Stop")
        break
    print("Hello, Number", i )

### Functions

In Python, you define a function as a function

>
    def addOne(x):
        return x + 1
    print(addOne(5)) # 6



