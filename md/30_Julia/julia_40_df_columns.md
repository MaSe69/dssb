---
layout: 30_julia
title: Julia DF Columns
permalink: /julia_columns

---

# Julia Dataframes - Columns

Here are the same basic functions as for Python:

- [Address](#address-columns)
- [Basic Arithmetics](#basic-arithmetics)
- [Subsets](#work-on-subsets)
- [Rename](#rename-columns)
- [Reorder](#reorder-columns)
- [Create](#create-columns)
- [Delete](#delete-columns)
- [Modify](#modify-columns)



## Address Columns

Address an existing column with its name in square brackets and quotes directly after the dataframe variable **and** use a bang (!) for the rows.

>
    df[!, "Horsepower"]

Alternatively, an existing column with a suitable columnName can be addressed 
>
    df.Horsepower

For instance, you can round a column with floats in at least these 2 notations:

>
    round.(df[:, "Acceleration"],digits=0)
    round.(df.Acceleration,digits=0)

Mind (once more) the broadcasting operator (.) .


If you do not know the column names, get their names

>
    columnNames = names(df)


Convert the type of a column, e.g. from float to int.

>
    df[:,:Acceleration ] = convert.(Int,round.(df.Acceleration,digits=0))

This is conversion is a bit more tricky in Julia, because Julia demands to decide how to handle the "0.5" case. Hence, first the float must be rounded, for instance, and then converted to integer.    


## Basic Arithmetics

### Multiply with a scalar

For scalars, just use the normal symbols: 

>
    df.Acceleration = df.Acceleration / 17    
    df[:, "Acceleration"] = df[:,"Acceleration"] / 17   


### Multiply a column with a column to get an additional column

Particularly, multiplying two columns to yield a third one in the same dataframe.

>
    df2[!,:C] = df2[!,:A] .* df2[!,:B]

The result here is an additional column with column name C that is the row-wise product of columns A and B.

Such column-with-column-multiplications have a lot of practical use cases.


### Multiply two columns to get an array

>
    df3 = df2.A .* df2.B 

The result here is a 1x2 array.

Such a multiplication might be rather rare in practice. It is listed here to clarify confusion, if you in fact intended to do a column by column multiplication to get a third column.     


