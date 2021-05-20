---
layout: 20_topic
title: Julia
permalink: /julia
---

# Julia (Dataframes.jl)

In Julia, the library for dataframes is fittingly clalled Dataframes.jl. 

## [Create dataframes](julia_createDF)

Create a new dataframe within the program
- from lists or arrays (created with Numpy)
- from a dictionary

## Download Data From External Sources

Download from the web,
- when download into a dataframe works smoothly
- when the 'object' first has to be downloaded using HTTP

Explore data 
- get to know some data sources
- describe (to get some statistics
- shape (to get the number or columns or rows)

## [Read datafrome from local disc](julia_saveDF)

Read to 
- limit the data: rows / columns
- deal with missing values
- read dates to get a timeseries

## [Operations on the entire dataframe](julia_operateOnDF)

Some of the operation of this type are: 
- Change all values of the dataframe simultaneously (except the index)
- Multiplying the dataframe with a number
- Adding or subtracting one dataframe from another dataframe
- Transpose a dataframe


## [Operate on Columns](julia_columns)

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

## Merge dataframes

After having cleansed and wrangled one dataframe, you might want to continue to aggregate. 
After having soaked out all info from that one dataframe, you might continue with merging it with one or several other dataframes. Merging with other dataframes can also become a business of mass production, particularly for time series.

