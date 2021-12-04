---
layout: 20_python
title: Python About
permalink: /python_annotations
---

# Annotations On Python Listing

Some deeper thoughts on the Python listing.


## Text output to console
>
    print("Hello, Dataframes in Python")

In Python, Strings are denoted by single or double quotation marks ('text' or "text").
For efficiency with conversion to Julia, here only double quotation marks are used.

>
    language = "Python"
    print("Hello, ", language)


## Strings

Let's start the Python journey with a console output like

>
    print("Hello World)

From there, we could replace the strings with variables, following the path of a typical tutorial.

A first hurdle might be to change a string, because strings are immutable. Common  workaround for immutable Strings: New string composed of parts of old string. I often need to convert different date formats, e.g. convert "202101" to "2021-01". This is can be done using slicing in this way:

>
    myStringNew = myString[:4] + "-" + myString[4:6]


As Strings are immutable, this also does not work: 
>
    language[1] = "C"


In Python, "String concatenation can simply be done with a plus ( + ) sign. 

>
    stringConcat = "Language: "  + language[1:]
    print(stringConcat)


## Float and Integer

Mind that 

>
    int(myFloat)
truncates the float, i.e. 123456,89 becomes 123456. Hence, in the context here, round it first.

Implicit type definition by representative + Type conversion

>
    n = 5
    x = 7.7
    y = n * x
    print(y)
    myInt = int(y)    ### Conversion is a bit straightforward
    print(myInt)
    print(type(language), type(n), type(y), type(myInt))


## Arrays

There are two ways to reverse the order of the array elements. The [::-1]-notation is convenient to use in Pandas.

You can slice an array specifying its start position, end position and the step size. 
For instance, between the second and forth of my specified cities, keep every second one:
>
    SomeCities = myCities[1:4:2]

When looping and not needing the key, you can replace the variable with an underscore "_".
>
    for _ , value in myDict.items():

### Loops

Python starts with 0-
Python needs indent, but does not need an 'end'

>
for i in range(4):
    if i > 1:
        print("Stop")
        break
    print("Hello, Number", i )    


## Comprehensions

Comprehensions can be used to compose column headers for new dataframes more efficiently.

Extracting elements by a specific condition from an array can be tricky, but it's often doable.
For instance, put every city to upper case that contains in its name either the letter r or l:

>
    cities_r = [city.upper() if "r" in city or "l" in city else city.capitalize() for city in myCities]

## Files

- Read and find: Read a file from a folder or find that file and return its folder, if found.
- Read all files from a folder.
- Save a file to a folder or create that folder first (after manual 'ok')



### Functions

In Python, you define a function as a 'definition' (def)

>
    def addOne(x):
        return x + 1
    print(addOne(5)) # 6

