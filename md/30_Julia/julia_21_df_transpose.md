---
layout: 30_julia
title: Julia DF Ops
permalink: /julia_transpose

---

# Transpose a Dataframe in Julia


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



