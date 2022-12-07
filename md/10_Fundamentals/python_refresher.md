---
layout: 20_python
title: Python Refresher
permalink: /python_refresher
---

# Python Refresher

Students starting with 'Data Science in Python' are expected to have successfully completed a Python fundamentals course. 
Here is a refresher of what I subsequently will use for data science tasks or of what I saw going wrong.
Certainly, everything here can and should be looked up elsewhere in more detail.

## Python Primitives

Well, let's start on how to correct when you had started with the wrong key board language settings, illustrating the trap of immutable Python strings and how to fix that.

>
    language = "Pzthon"
    language = language[:1] + "y" + language[2:]
    print("Hello", language)


The print command accepts both '+' and ',' to concatenate strings. When '+' is used, a number must be converted to a string first.

>
    x = 123.4
    y = 123.5
    print("First number: ", x)
    text2 = "Second number: " + str(y)
    print(text2)

Python turns even a 123.9 into an integer of 123. 

>
    myIntX = int(x)
    myIntY = int(y)
    print(myIntX, myIntY)

If you want the 123.5 to be rounded up to 124, you can do it this way.

>
    myRoundedX = round(x, 0)
    myRoundedY = round(y, 0)
    myIntX = int(myRoundedX)
    myIntY = int(myRoundedY)
    print(myIntX, myIntY)

Finally, you might want to check the types of the variables.

>
    print(type(language), type(x), type(myRoundedX), type(myIntX))


## Python Functions

I will use the same list a few times below, hence, I put it to a separate file. In the subsequent programs, I import the function from that file. 

>
    def getNames():
        names = ["David", "Nicola", "Karen", "John", "Jack", "Fiona", "Olivia"]
        return names

## Python Lists 

Let's get these names first.

>
    names = getNames()

Let's start with printing the second name. You remember here the latest that Python starts numbering with 0.
>
    print(names[1])

Print 3 names starting with the third name.
>
    print(names[2:5])

Print the second last name
>
    print(names[-2])

Get length of the list, i.e. the number of elements in the list. Further, get half of the list.
>
    listLength = len(names)
    listLengthHalf = int(round(listLength / 2, 0))
    print("Length of the list " + str(listLength))
    print("Half of the length of the list " + str(listLengthHalf))

Get the second half of the list.
>
    lastHalf = names[listLengthHalf:listLength]

Get every second element of list
>
    everyOther = names[::2]

Starting with loops, let's print out a "Hello" with the first name for each element of the list.
>
    for name in names:
        print("Welcome, " + name + "!")

Add an incremented integer starting with 1.
>
    for i, name in enumerate(names):
        print(name, "you get the number ", i + 1)

Adding two lists is a very common use case. I created a second function with a list of common French first names. Obviously, adding only one element comes down to adding a second list with this element.
>
    namesFrench = getNamesFrench()
    allNames = names + namesFrench
    print(allNames)

Unfortunately, creating a list with random integer seems to be a bit tricky. It requires to introduce the library numpy. <br>
Numpy works with array. I will try to call the 'arrays' in Python 'lists. Numpy arrays can be converted to Python lists using the 'tolist()' command. 
Further, this command leads to a list in a list. Hence, I need to address the first element of this list. Finally, I get the list of random integers. 
The first two parameters specify the lower and upper boundary of these integers

>
    import numpy as np
    np.random.seed(0)
    randomHeights = np.random.randint(170, 190, (1, len(names))).tolist()[0]


## Comprehensions

Get all names with a substring. You might want to use this later to get all columns with a substring in their headers, e.g. '2022'. 
>
    substring = 'n'
    namesWithSubString = [name for name in names if substring in name]

You might notice that a name starting with a capital N is not in the list above. If you want to include these names, too, try this version.

>
    namesWithSubString = [name for name in names if (substring in name or substring.upper() in name)]

You can also do something directly in the comprehension depending on a condition.
>
    namesUpper = [name.upper() if substring in name else name.capitalize() for name in names]

## Dictionaries

Using 'dict' and 'zip', you can easily create a dictionary from two lists. The first lists contains the keys and the second list the values.

>
    namesDict = dict(zip(names,randomHeights))
    print(namesDict)

Certainly, you can use a less elegant way and loop over the first array adding the values as you go.
>
    namesHeight = {}
    for i, name in enumerate(names):
        namesHeight[name] = np.random.randint(160,190)

You can print out both the keys and the values,
>
    for key, value in namesHeight.items():
        print(key, value)

or just the keys or the values, omitting the other, respectively, with an underscore.
>
    for key, _ in namesHeight.items():
        print(key)
    
If you are not happy with your dictionary anymore, you might want to go back to lists.
>
    myKeys = list(namesHeight.keys())
    myValues = list(namesHeight.values())

