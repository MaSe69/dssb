---
layout: 20_python
title: Python Listing
permalink: /python_listing
---

## Altair Listing

These are just some hopefully useful hints when using Python with Pandas.

|  Object |  How to | Coding Hint | 
| :---            |    :--------   |  :--- |  :--- |  
| Strings | Modify| myString[0:4] + "-" + myString[4:6] |
| Float | round a larger currency value to thousands| int(round(myFloat,-3)) |
| Array | create an array with 10 integers| list(range(0,10)) |
| Array | reverse the order of its elements| myArr[::-1].reverse() |
| Array | loop over array and get index| for i, city in enumerate(myCities): |
| Dictionary | create a dict in a loop| myDict[city[:1]] = city |
| Dictionary | loop over array| for key, value in myDict.items(): |
| Comprehension | get list elements for a condition| [city for city in myCities if "r" in city] |
