---
layout: 30_julia
title: Julia DF Columns
permalink: /julia_columns

---

# Julia Dataframes - Columns

Here are the same basic functions as for Python:

- [Address](#address-columns)
- [Basic Arithmetics](#basic-arithmetics)
- [Rename](#rename)
- [Reorder](#reorder)
- [Insert](#insert)
- [Modify](#modify)
- [Delete](#delete)


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

### Insert ( =add ) a column at the end

Specify a unique name in square brackets and quotes.

>
    df[!,:D] .= 17

You can use existing columns to create new ones, including more complex computations
>
    df[!,:E] = 7 * df.A + df.D

Alternatively, a function can be used. Here, the new column Y is the sum of columns A and B.
>
    df = transform(df, [:A, :B] => (+) => :Y)

### Insert a new column at specific position

For columns that should go to a specific position, you can directly insert a new column at a position.
>
    arr = [1,1,1]
    insertcols!(df, 2, :I => arr)


This is more efficient than to append at the end and then re-order the columns.


### Special case

Append a column with the sum or the mean of all columns (that are not in the index)
>
    df[!,:Sum] = sum(eachcol(df))
    df[!,:Mean] = mean(eachcol(df))


## Modify

### Replace all values in a columns

Often, you just want to replace one value in a given column by another value

>
    df.A = replace(df[!,:A], 2 => 33)


### Modify column B based on values in column A

Sometimes, you want to modify a value in a specific column depending on the value in another column. 
For instance, if the value in column C equals 1, you want the respective value in column A to equal 17.

> 
    df[!,:A][df[!,:C] .== 1] .= 17

Here, all values in column C are set to 18, if column B has value 1.
>    
    df[df.B .== 1,:C] .= 18


### Create a new column B based on values in column A

I have not found a Julia solution so far. All found solutions first create a column and then change it.

## Delete

Delete columns with the select command combined with Not
>
    dropCols = [:B, :C] 
    df = select!(df, Not(dropCols))

Mind the alternative to continue to work on the relevant subset of columns instead of deleting the obsolete columns.
For, instance, if you just want to keep the columns D and E.

>
    df = df[:, [:D, :E]]

