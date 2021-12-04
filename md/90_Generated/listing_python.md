---
layout: 20_python
title: Python Listing
permalink: /python_listing
---

## Python Listing

These are just some hopefully useful hints when using Python with Pandas.

|  Object |  How to | Coding Hint | Link to Details |
| :---            |    :--------   |  :--- |  :--- |  
| Strings | Modify| myString[0:4] + "-" + myString[4:6] | [Strings](python_annotations)  |
| Float | round a larger currency value to thousands| int(round(myFloat,-3)) | [Float](nan)  |
| Array | create an array with 10 integers| list(range(0,10)) | [Array](python_annotations#array)  |
| Array | reverse the order of its elements| myArr[::-1].reverse() | [Array](python_annotations#array)  |
| Array | loop over array and get index| for i, city in enumerate(myCities):python_annotations#array | [Array](nan)  |
| Dictionary | create a dict in a loop| myDict[city[:1]] = city | [Dictionary](nan)  |
| Dictionary | loop over array| for key, value in myDict.items(): | [Dictionary](nan)  |
| Comprehension | get list elements for a condition| [city for city in myCities if "r" in city] | [Comprehension](nan)  |

This table was generated using a dataframe.

Find details in the [Python Listing Annotations](python_annotations).
