---
layout: 30_julia
title: Julia DF Ops
permalink: /julia_df_ops

---

# Operations on the Entire Dataframe

Here are some selected operations on the entire dataframe.


## Meta Data

Get the Number of rows and columns of a dataframe df using
>
    size(df)

Get details about the columns of the dataframe df

>
    describe(df)    

<center>
<br>
{% include images/image.html imagePath = "../assets/images/img_blog/Julia/Julia_describe.png" thisWidth ="800px"%}
Get the columns, their types and some statistics, when you describe the Julia dataframe.
</center>  


## Basic Arithmetics

Let's define a new, small dataframe df1. A dataframe based on a 2x2 unity matrix might do.

>
    df1 = DataFrame(A = [1, 0], B = [0, 1] )

### Multiply with a scalar

Multiply the dataframe with pi.<br>
Subtract the square root of 2.

>
    df2 = df1 .* π
    df2 = df1 .- sqrt(2)

Mind the broadcasting operator!

### Multiply with a column to get an additional column

Particularly, multiplying two columns to yield a third one in the same dataframe.

>
    df2[!,:C] = df2[!,:A] .* df2[!,:B]

The result here is an additional column with column name C that is the row-wise product of columns A and B.

Such column-with-column-multiplications have a lot of practical use cases.


### Multiply two columns to get an array

>
    df3 = df2.A .* df2.B 
    println("df3 $df3")

The result here is a 1x2 array.

Such a multiplication might be rather rare in practice. It is listed here to clarify confusion, if you in fact intended to do a column by column multiplication to get a third column.


## Matrix operations

A matrix contains the body of a dataframe. 
Some operations on a Julia dataframe are not available, but can be retrieved by extracting this matrix and then re-assembling the dataframe.


### Transpose

There is no built-in transpose command in Julia Dataframes. You need to extract the matrix, transpose the matrix and re-built a dataframe. 

You can get the matrix, ma, from the dataframe with the **matrix** command

>
    ma = Matrix(df)

Then, you transpose the matrix

>
    mat = transpose(ma)
    mat = ma'

The matrix mat holds the transposed matrix. 

Finally, you need to get back to a new dataframe, dfT, 

>
    dfT = DataFrame(mat, :auto)

and to adjust the column names later. Mind the second parameter ("auto") which is required in higher versions of DataFrames.


### Invert

Do the same as for transpose, but invert the matrix.

>
    mai = inv(ma)


