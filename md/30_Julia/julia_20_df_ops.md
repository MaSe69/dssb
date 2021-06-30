---
layout: 20_python
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

### Multiply with a vector

Particularly, multiplying two columns to yield a third one in the same dataframe.

>
    df2[!,:C] = df2[!,:A] .* df2[!,:B]

The result is an additional column with column name C that is the row-wise product of columns A and B.


### Multiply with a column (or other suitable vector)

>
    df3 = df2.A .* df2.B 
    println("df3 $df3")


The result is a 1x2 array.





