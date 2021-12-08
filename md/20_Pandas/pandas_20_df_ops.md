---
layout: 20_python
title: Pandas DF Ops
permalink: /pandas_df_ops

---

# Operations on the Entire Dataframe

Here are some selected operations on the entire dataframe.

## Meta data about the dataframe

First, let's get some info about the dataframe, i.e. the so-called meta data.

### Get number of rows

The function 'shape' - to be used without parenthesis - returns the number of columns or rows. 

>
    nrRows = df.shape[0]
    print("Number of rows:", nrRows)

### Get number of columns

Get the number of columns with the second element of shape. 

>
    nrColumns = df.shape[1]


### Get data types of columns

The data type of each column is listed with 'dtypes'

>
    myDataTypes = df.dtypes

### Get some statistics on the dataframe content

The function 'describe' - to be used with parenthesis - returns some statistics on the numerical values of the dataframe.

>
    someStatistics = df.describe()

## Application to all cells

### Transpose dataframe

In Python, there is a transpose operator 'T'. 

>
    dfT = df.T

In the transposed dataframe, the element [i,j] in df is at [j,i] in the transposed dataframe dfT.<br>
When there is an automatically created index, i.e. 0, 1, 2, ... , it will be moved to the column names. Usually, this is not wanted, so set the index first to the requested new header.
In the cars, this would mean:

> 
    df = df.set_index("Name")
    dfT = df.T

As a result, the names of the cars, which were in the rows of the first column, are in the column names.

### Fill all missing values

Some dataframes contain only numerical values, except maybe for the index.
Then, it can be efficient to set all missing values to zero.

>
    df = df.fillna(0)

