---
layout: 20_python
title: Python About
permalink: /python_about
---

# Python About

Some explanations and deeper thoughts on my Python listing.

## Strings

Let's start the Python journey with a console output like

>
    print("Hello World)

From there, we could replace the strings with variables, following the path of a typical tutorial.

A first hurdle might be to change a string, because strings are immutable.
I often need to convert "202101" to "2021-01". This is can be done using slicing in this way:

>
    myStringNew = myString[:4] + "-" + myString[4:6]


## Float and Integer

Mind that 

>
    int(myFloat)
truncates the float, i.e. 123456,89 becomes 123456. Hence, in the context here, round it first.

## Arrays

There are two ways to reverse the order of the array elements. The [::-1]-notation is convenient to use in Pandas.

You can slice an array specifying its start position, end position and the step size. 
For instance, between the second and forth of my specified cities, keep every second one:
>
    SomeCities = myCities[1:4:2]

When looping and not needing the key, you can replace the variable with an underscore "_".
>
    for _ , value in myDict.items():

## Comprehensions

Extracting elements by a specific condition from an array can be tricky, but it's often doable.
For instance, put every city to upper case that contains in its name either the letter r or l:

>
    cities_r = [city.upper() if "r" in city or "l" in city else city.capitalize() for city in myCities]



