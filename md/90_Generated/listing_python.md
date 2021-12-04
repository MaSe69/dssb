---
layout: 20_python
title: Python Listing
permalink: /python_listing
---

## Python Listing

These are just some hopefully useful hints when using Python with Pandas.

|  Object |  How to | Coding Hint | Link to Details |
| :---            |    :--------   |  :--- |  :--- |  
| Strings | Modify| myString[0:4] + "-" + myString[4:6] | [Strings](python_annotations#primitives)  |
| Float | round a larger currency value to thousands| int(round(myFloat,-3)) | [Float](python_annotations#primitives)  |
| Arrays | create an array with 10 integers| list(range(0,10)) | [Arrays](python_annotations#array)  |
| Arrays | reverse the order of its elements| myArr[::-1].reverse() | [Arrays](python_annotations#arrays)  |
| Arrays | loop over array and get index| for i, city in enumerate(myCities): | [Arrays](python_annotations#arrays)  |
| Dictionaries | create a dict in a loop| myDict[city[:1]] = city | [Dictionaries](python_annotations#Dictionaries)  |
| Dictionaries | loop over array| for key, value in myDict.items(): | [Dictionaries](python_annotations#Dictionaries)  |
| Comprehensions | get list elements for a condition| [city for city in myCities if "r" in city] | [Comprehensions](python_annotations#comprehensions)  |
| Files | Find file| or root, dirs, files in os.walk(path): | [Files](python_annotations#files)  |
| Files | create folder| os.mkdir(path) | [Files](python_annotations#files)  |

This table was generated using a dataframe. Find here explanations [about Python](python_about).
