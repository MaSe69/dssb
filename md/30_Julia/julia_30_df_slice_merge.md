---
layout: 30_julia
title: Julia DF Slice Merge
permalink: /julia_slice_merge

---

# Copy, Slice and Merge

It is a common vice to leave a lot of data in a table or dataframe, because the skills are missing to park them somewhere else and to only get them back when needed. 


## Rename vs. Shallow Copy vs. Deep Copy

Sometimes, you need to rename a dataframe and sometimes you need to make a real copy. Problems can emerge when you intend to do the one, but technically you do the other.

Example: You slice a dataframe and rename that particular fraction, instead of copying it. Then, you also change the original dataframe, which might lead to wrong results later that are difficult to find.

In Julia, there is quite some implicit logic in this distinction. 

You only rename a dataframe when you equal it to a new name, e.g. 

> 
    df2 = df

A so-called "shallow copy" of the dataframe is made with the standard copy command.
>
    dfCopy = copy(df)


A shallow copy copies some but not all of the dataframe.


In order to make a real, independent copy of your dataframe, you need to use **deepcopy**

>
    dfDeepCopy = deepcopy(df)

Changes to dfDeepCopy do not affect df.


## Slice

Let use again the dataframe holding the cars data.

>
    filename = "cars.csv"
    path = "./ZZ_Data/"
    relname = path * filename
    df = CSV.read(relname, DataFrame)

Differences to Python include: 
- You need always to specify both **rows and columns**    
- You need to specify the first and last element, if you do not select all. 
- The last element is specified using **end**

### Columns

Get selected column numbers
>
    colNumbers = [1, 2, 3, 5, 8]
    df2 = df[:, colNumbers]


Mind that you need to specify the rows with the colon (:) sign, i.e. here you select all rows.


Get selected column names

>
    keepCols = [:Name, :Cylinders, :Horsepower, :Origin]
    df2 = df[:, keepCols]

Instead of slicing, the **select** command can be used as well

>
    keepCols = [:Name, :Cylinders, :Horsepower, :Origin]
    dfS = select(df, keepCols)


### Rows

Get selected row numbers

Create a dataframe, d2, that contains rows 3, 4, 5, 6 and 7.
>
    df2 = df[3:7, :]

Create a dataframe, 2, that contains every 100th row.

>
    df2 = df[1:100:end, :]

### Rectangular

A rectangular selection from with the origina dataframe

>
    df3 = df[4:8, 5:7]











