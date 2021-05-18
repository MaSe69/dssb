---
layout: 10_topic
title: Pandas
permalink: /pandas
---

# Cheat Sheat

You can find on Github complete solutions as Jupyter Lab. 

- [Jupyter Lab - Pandas on Github](https://github.com/MaSe69/dataframes/tree/master/dfPython)

For a quick reference (or cheat sheet), I put the essential parts of code here.
Often, you (and I) just need to look up the exact syntax.

## Getting Started

### Python Refresher

- Type conversions in Python
- How to handle unchangeable strings?


### Numpy

- Lists: Fast creating and operating
- Create multi-dimensional arrays and work with them
- Random Numbers


## One Dataframe

### [Create dataframes](pandas_createDF)

Create a new dataframe within the program
- from lists or arrays (created with Numpy)
- from a dictionary
- get to the same dataframe as with Julia


### Download Data From External Sources

Download from the web,
- when download into a dataframe works smoothly
- when the 'object' first has to be downloaded using HTTP

Explore data 
- get to know some data sources
- describe (to get some statistics
- shape (to get the number or columns or rows)

### [Read datafrome from local disc](pandas_saveDF)

Read to 
- limit the data: rows / columns
- deal with missing values
- read dates to get a timeseries

### [Operations on the entire dataframe](pandas_operateOnDF)

Some of the operation of this type are: 
- Change all values of the dataframe simultaneously (except the index)
- Multiplying the dataframe with a number
- Adding or subtracting one dataframe from another dataframe
- Transpose a dataframe


### [Operate on Columns](pandas_columns)

Some of the operation on columns are: 
- Rename the columns
- Re-order the columns
- Add columns (at the end)
- Insert columns at a specific position
- Delete columns


### Operate on Rows

Sorting is one of the most frequent operations on rows. (There is rarely the need for sorting columns).

Some further operation on rows are: 
- selecting a subset on row by slicing or on condition
- deleting rows
- adding or copying rows


### Operate on Cells

Changing the cell (i,j) should be avoided when ever possible.
There is almost always a way to get around addressing a particular cell.
Almost always, but in rare cases, you really need to get to the one or other odd cell in a big dataframe, typically on given conditions. Though possible, it is cumbersome. 

## Two Dataframes

### Aggregation

Grouping is usually done in two steps. First, you group by one or several columns. Second, you apply a statistical operation, which might be as simple as a sum or a mean to that grouping. 


### Merge

After having cleansed and wrangled one dataframe, you might want to continue to aggregate. 
After having soaked out all info from that one dataframe, you might continue with merging it with one or several other dataframes. Merging with other dataframes can also become a business of mass production, particularly for time series.



A revealed pattern in data science consists of 3 steps
- split
- operate (aggregate)
- merge


# General Info on Python + Pandas


The Python library Pandas had its initial release in 2008, [see Wikipedia](https://en.wikipedia.org/wiki/Pandas_(software)). 

Parts of its history is described by its inventor 
[Wes McKinney | Youtube ](https://www.youtube.com/watch?v=kHdkFyGCxiY). Wes McKinney published a book on Pandas which remarkably is not named Pandas, but "Python for Data Analysis". 
The coding of this book is available on Gibhub:
-  [https://github.com/wesm/pydata-book](https://github.com/wesm/pydata-book)

Wes McKinney was employed at that time at a financial department which might explain the good support of time series in Pandas. Pandas grew in an environment of Excel, Matplab and R.  


## Reference and Python community

The official documentation is good and helpful

[https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html)

There is no need to shy away from it and to search first in secondary sources (as it is true for other official documentations)

Stackoverflow has emerged as THE reference for Python and Pandas. This might not be noteworthy, if true for Julia dataframes. Julia dataframes can be found on stackoverflow, but rather rarely. The dataframe tag in stackoverflow is about hundred thousand questions, with predominantly Pandas dataframes being asked for.


