---
layout: 10_topic
title: Pandas DF Ops
permalink: /pandas_df

---

# Operations on the Entire Dataframe

You can make some operations on the entire dataframe.

As a prerequesite, apart from the index, all cells need to fulfill the prerequites of the operation.
## Preparing the dataframe

As the prerequesite of suitabililty of the dataframe might only hold true for small dataframes, as preparation
you have at least these option:

- Move all other columns to temporarily to the index.
- Slice the dataframe

### Indices

The first column of a Pandas dataframe is the index - just integer numbers.
You can specify one or more columns as this index, which then substitute Pandas' index.

>
    df = df.set_index(myColumns[:k])

with k being the column number that ends the index.
Perform the operation and then reset the index.

See the section [Operate on Columns](pandas_columns) for further details.

Applying an operation on the dataframe, only the non-indexed columns are affected. 

### Slice

You can define a 'rectangle' of your dataframe to be a new dataframe - and apply the operation only to that new .

>
    dfSlice = df[r1:r2; c1:c2].copy()

with r1 and r2 being the first and last row, c1 and c2 being the first and last column.

Mind that without the copy your operation might also affect the original dataframe. 

## Rename or Copy

You might want to rename your dataframe or to make a real copy.

>
    df_New = df          # Does not create a copy, just another name
    df_New = df.copy()   # Create a real copy 

### Transpose a dataframe

>
    df = df.T

However, there is no inversion of a dataframe.
Possible workaround: extract to a Numpy array. 

## Meta data about the dataframe

'shape' returns the number of columns or rows. 

>
    print("Number of (rows, columns):", df.shape)

'describe' returns meta data on the dataframe.

>
    dfMetaData = df.describe()

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

### Fundamental Operatoins

Multiply (or divide) by a number

>
    df = 3.141529 * df

Modulo operation
>
    df = df % 1

Adding or subtracting a suitable other dataframe
>
    df = df2 + df1
    df = df2 - df1




