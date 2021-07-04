---
layout: 30_julia
title: Julia DF Columns
permalink: /julia_columns

---

# Julia Dataframes - Columns

Here are the same basic functions as for Python:

- [Address](#address-columns)
- [Basic Arithmetics](#basic-arithmetics)
- [Rename](#rename-columns)
- [Reorder](#reorder-columns)
- [Create](#create-columns)
- [Delete](#delete-columns)
- [Modify](#modify-columns)



## Address Columns

Get the existing column names
>
    columnNames = names(df)

Address an existing column with its name **without** copying, see [DataFrames and !](https://bkamins.github.io/julialang/2021/01/30/bang.html)
>
    df[!, :col1], df.col1

Address an existing column **with** copying,
>
    df[:, :col1]

In Julia, you can select all columns of a specific type.
>
    dfText = df[!, names(df, String)]
    dfFloats = df[!, names(df, Float64)]

Such a selection can substitute for the missing index features in Python, i.e. before applying an operation that is not possible for Strings, you can first de-select all columns holding Strings.


## Basic Arithmetics

Often, you cannot apply an operation on the complete dataframe, but only a set of selected rows. 
Alternatively, you can create a new dataframe with the specified columns and merge the result back later.

### Multiplying with a scalar

For scalars, just use the normal symbols: 
>
    df.Acceleration = df.Acceleration / 17    
    df[:, "Acceleration"] = df[:,"Acceleration"] / 17   


Select a subset of columns and apply an operation on it. 
>
    selectedColumns = ["colname1", "colname2"]
    df[selectedColumns] = df[:,selectedColumns] * 100.0        


### Converting a type

Often used, round floats or convert floats to integers

>
    df[:,:Acceleration ] = convert.(Int,round.(df.Acceleration,digits=0))

Mind (once more) the broadcasting operator (.) .
This is conversion is a bit more tricky in Julia, because Julia demands to decide how to handle the "0.5" case. Hence, first the float must be rounded, for instance, and then converted to integer.    


### Multiply a column with a column to get an additional column

Particularly, multiplying two columns to yield a third one in the same dataframe.

>
    df2[!,:C] = df2[!,:A] .+ df2[!,:B]
    df2[!,:C] = df2[!,:A] .* df2[!,:B]

The result here is an additional column with column name C that is the row-wise product of columns A and B.

Such column-with-column-multiplications have a lot of practical use cases.


### Multiply two columns to get an array

>
    df3 = df2.A .* df2.B 

The result here is a 1x2 array.

Such a multiplication might be rather rare in practice. It is listed here to clarify confusion, if you in fact intended to do a column by column multiplication to get a third column.     



## Rename

Rename specific single columns, 

>
    df = rename(df, Dict(:Origin => "Country"))

Rename all columns, by specifying a list of unique values

>
    newColnames = [:col1, :col2, :col3, :col4, :col5, :col6, :col7, :col8, :col9]
    rename!(df,newColnames)


A step in beautification is to convert all column names to a similar format, e.g. to start with a capital letter.

All column names capitalized or in upper case
>
    df = rename(uppercase, df)
    df = rename(uppercasefirst, df)    


## Reorder 

Use the of **existing column names** to re-order the columns, by specifying a new, complete sequence
>
    reorderedCols = [:col9, :col8, :col3, :col4, :col5, :col6, :col7, :col2, :col1]
    df = df[1,reorderedCols]

You can reverse the sequence of the columns as follows
>
    df = df[:,reverse(names(df))]



## Insert

### Add a column at the end

Specify a unique name in square brackets and quotes.

>

You can use existing columns to create new ones. 

More complex computations are possible.

>

### Insert a new column at specific position

For columns that should go to a specific position, you can directly insert a new column at a position.

>

This is more efficient than to append at the end and then re-order the columns.


## Special 

### Special case

Append a column with the sum of all columns (that are not in the index)
>


## Delete


Delete columns with the drop command:

>

Alternative notation,

> 


Warning: If deletion reduces the Pandas dataframe to just one column, Pandas regards it as a vector. A vector can have different properties, possibly leading to error messages.

Mind the alternative to continue to work on the relevant subset of columns instead of deleting the obsolete columns.


## Modify

### Replace an existing value in a specific column

Name the column and replace the value in a row for a specified condition

>


### Modify column B based on values in column A

Change the value in a column, here 'Environment', for some rows on condition of values in another column, here 'Miles_per_Gallon' 

> 


All cars with more than 20 miles per gallon get the ok here.

### Create a new column B based on values in column A

Create a new column with values specified in a dictionary before.

>

A new column with abbreviations was created.

