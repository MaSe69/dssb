---
layout: 10_topic
title: Pandas
permalink: /pandas
---

# Pandas


The Python library Pandas had its initial release in 2008, [see Wikipedia](https://en.wikipedia.org/wiki/Pandas_(software)). 

Parts of its history is described by its inventor 
[Wes McKinney | Youtube ](https://www.youtube.com/watch?v=kHdkFyGCxiY). Wes McKinney published a book on Pandas which remarkably is not named Pandas, but "Python for Data Analysis". 
The coding of this book is available on Gibhub:
-  [https://github.com/wesm/pydata-book](https://github.com/wesm/pydata-book)

Wes McKinney was employed at that time at a financial department which might explain the good support of time series in Pandas. Pandas grew in an environment of Excel, Matplab and R.  


# Python

Admittedly, you cannot jump straight into data frames without knowing a bit about Python and its environment. 

You therefore find a refresher on Python as  on my Github. 
Find here my respective coding on Github in Jupyter Lab. 

- [Jupyter Lab - Pandas on Github](https://github.com/MaSe69/dataframes/tree/master/dfPython)

I worked through most of Wec McKinneys book and coding. As said before, I just need one solution that works in my context. If my solution does not work for you, you will find it easily in the comprehensive literature.

## Reference and Python community

The official documentation is good and helpful

[https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html)

There is no need to shy away from it and to search first in secondary sources (as it is true for other official documentations)

Stackoverflow has emerged as THE reference for Python and Pandas. This might not be noteworthy, if true for Julia dataframes. Julia dataframes can be found on stackoverflow, but rather rarely. The dataframe tag in stackoverflow is about hundred thousand questions, with predominantly Pandas dataframes being asked for.


## Create dataframes

It seems to be natural to start with an empty dataframe and then fill it later. 
My intuition is backed by a highly voted question on Stackoverflow: [Creating an empty pandas dataframe - then filling it](
https://stackoverflow.com/questions/13784192/creating-an-empty-pandas-dataframe-then-filling-it).

There is a 'world' before dataframes. You should have that matrix first, before you wrap it into columns and rows. Later, for performance reasons, you might extract that matrix again and work on it and convert it back to a dataframe.
Creating dataframes from scratch is for good reason hence not supported by Pandas.

In Python, you have typically lists or dictionaries from which dataframes can be easily created.

- [Create dataframes](pandas_createDF)


## Save and read dataframes

[save and read dataframe](pandas_saveDF)


## Operate on the whole dataframe

[operate on whole dataframe](pandas_operateOnDF)

## Columns

[columns](pandas_columns)


## Grouping


## Merging

