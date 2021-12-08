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

