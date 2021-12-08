---
layout: 20_python
title: Pandas DF Ops
permalink: /pandas_df_ops_old

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


### Basic Arithmetics

Multiply (or divide) by a number

>
    df = 3.141529 * df


Adding or subtracting a suitable other dataframe
>
    df = df2 + df1
    df = df2 - df1

The index in Pandas provides a convenient possibility to put all columns that shall not be subjected to an operation temporarily to that index. After the operation, you can then reset the index.


### Transpose

>
    df = df.T

However, there is no inversion of a dataframe.
Possible workaround: extract to a Numpy array.     


### Indices

The first column of a Pandas dataframe is the index - just integer numbers.
You can specify one or more columns as this index, which then substitute Pandas' index.

>
    df = df.set_index(myColumns[:k])

with k being the column number that ends the index.
Perform the operation and then reset the index.

See the section [Operate on Columns](pandas_columns) for further details.

Applying an operation on the dataframe, only the non-indexed columns are affected. 


## Operations on numerical values

### Fill all NaN with a different value
>
    df = df.fillna(0)

### Change the type of all columns

Convert floats to a currency-like format, i.e. two decimals only,
>
    df = df.astype(float).round(2)

Convert all numbers  to integers.
>
    df = df.astype(int)

Convert all numbers to integers and round to 1000s. 
>
    df = df.astype('int32').round(-3)

Examples: 
{% include images/image.html imagePath = "../assets/images/img_blog/opTables_Integers.png" imageCaption = "All values converted to integers and rounded to 10s."%}

