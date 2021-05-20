---
layout: 21_python
title: Pandas
permalink: /pandas
---

# Python (Pandas)

>
    You don't need to know all solutions. Just one that works for you.


[Pandas](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html) is the library for dataframes in Python.<br>
Consult the [Pandas Jupyter](https://github.com/wesm/pydata-book) examples provided by the master of Pandas, [Wes McKinney](https://wesmckinney.com/), for  many solutions.

## [Create dataframes](pandas_createDF)

Create a new dataframe within the program
- from arrays or lists
- to compare with Julia

## [Download Data](pandas_downloads)

Download from the web,
- when download into a dataframe works smoothly
- when the 'object' first has to be downloaded using HTTP

## [Read data](pandas_saveDF)

Read to 
- limit the data: rows / columns
- read timeseries
- deal with missing values


## [Operations on the entire dataframe](pandas_operateOnDF)

Some of the operation of this type are: 
- Change all values of the dataframe simultaneously (except the index)
- Multiplying the dataframe with a number
- Adding or subtracting one dataframe from another dataframe
- Transpose a dataframe


## [Operate on Columns](pandas_columns)

Some of the operation on columns are: 
- Rename the columns
- Re-order the columns
- Add columns (at the end)
- Insert columns at a specific position
- Delete columns


## Operate on Rows

Sorting is one of the most frequent operations on rows. (There is rarely the need for sorting columns).

Some further operation on rows are: 
- selecting a subset on row by slicing or on condition
- deleting rows
- adding or copying rows

## Merge dataframes

After having cleansed and wrangled one dataframe, you might want to continue to aggregate. 
After having soaked out all info from that one dataframe, you might continue with merging it with one or several other dataframes. Merging with other dataframes can also become a business of mass production, particularly for time series.

