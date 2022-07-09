---
layout: 20_python
title: Python About
permalink: /python_annotations
---

# Annotations On Python 

Assumingly, you are familiar with all the objects below. Here are little reminders on some features helpful when using Pandas.


## Text output to console
>
    print("Hello, Dataframes in Python")

In Python, Strings are denoted by single or double quotation marks ('text' or "text").
Whe also coding in Julia, you might want to use only double quotation marks.

>
    language = "Python"
    print("Hello, ", language)


## Primitives

Let's start the Python journey with a console output like

>
    print("Hello World)

From there, we could replace the strings with variables, following the path of a typical tutorial.

A first hurdle might be to change a string, because strings are immutable. Common  workaround for immutable Strings: New string composed of parts of old string. I often need to convert different date formats, e.g. convert "202101" to "2021-01". This is can be done using slicing in this way:

>
    myStringNew = myString[:4] + "-" + myString[4:6]


As Strings are immutable, this particularly does not work: 
>
    language[1] = "C"


In Python, "String concatenation can simply be done with a plus ( + ) sign. 

>
    stringConcat = "Language: "  + language[1:]
    print(stringConcat)


On Float and Integer, mind that 

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

Loop over an array as such 

> 
    for i in range(2, 12):
        <do something>

You can also iterate over objects (and count them)

> 
    for i, object in enumerate(objects):
        <do something>

(Mind that Python starts with 0 and Julia starts with 1).

There are two ways to reverse the order of the array elements. The [::-1]-notation is convenient to use in Pandas.

You can slice an array specifying its start position, end position and the step size. 
For instance, between the second and forth of my cities, keep every second one:
>
    SomeCities = myCities[1:4:2]

The meaning is: [start, end, step]
(Mind that in Julia, it is [start, step, end])


## Dictionaries

When looping over a dictionary and not needing the key, you can replace the variable with an underscore "_".
>
    for _ , value in myDict.items():


## Comprehensions

Comprehensions can be used particularly to compose column headers for new dataframes more efficiently.

Extracting elements by a specific condition from an array can be tricky, but it's often doable.
For instance, put every city to upper case that contains in its name either the letter r or l:

>
    cities_r = [city.upper() if "r" in city or "l" in city else city.capitalize() for city in myCities]


## Functions

In Python, you define a function as a 'definition' (def)

>
    def addOne(x):
        return x + 1
    print(addOne(5)) # 6


## Files

I had wasted so much time to 
- find files that I knew to exist, but the folder name got broken.
- read files by name from a folder, though I needed all the files in that folder.
- create a new folder, e.g. for a new date, before being able to save a plot to that folder.

Here are the decisive coding hints, for you to save that time.

### Read or find

Read a file from a folder or try to find that file in a path and return its folder, if found.

>
    import os
    ...
    path = <yourPath>
    for root, dirs, files in os.walk(path):
        for name in files:
            if name == myFilename:
                fullpathname = os.path.join(root, name)
                print(root, dirs, fullpathname)
                return(root, fullpathname)


### Read all files from a folder
    
Read all files or files of a specific extension, e.g. "csv" or "png".


>    
    import glob
    ...
    csvWanted = path + "/*." + extension 
    files = glob.glob(csvWanted)


### Save a file to a folder or create that folder first

If the attempt to save a file in a folder, but the folder does not exists, an error is raised.
This error can be caught and, if it is really the missing folder, the program shall create that folder.
I like to been asked first - and confirm - before the folder is created. Sometimes, the new folder has a spelling error, and it is a good point here to detect such  errors.

>
    import os, sys
    ...
    try:
        df.to_csv(path, ...)
    except:
        exc_type, _ , _ = sys.exc_info()        
        if exc_type.__name__ == "FileNotFoundError":
            print("Folder ", path , " does not exist.")
            answer = input("Create this path? (Press 'y' to create, else exit.)")
            if answer.lower() in ["y","yes"]:
                os.mkdir(newFullPath)


