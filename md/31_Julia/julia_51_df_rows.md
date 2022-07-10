---
layout: 30_julia
title: Julia DF Rows
permalink: /julia_rows
---


# Julia Dataframes - Rows

Rows

- [Address](#address-rows)
- [Subsets](#work-on-subsets)
- [Sort](#sort)
- [Create](#create)
- [Delete](#delete)



## Address Rows

You can address a row with its position given as an integer

>
    n = 5
    row = df[n,:])


## Work on Subsets

### First or Last Rows

For a bulk of rows from the beginning or the end of the existing dataframe, you can create a new dataframe:

>
    dfFirst_7_Rows = first(df,7)

>
    dfLast_4_Rows = last(df,4)


### Generic Subsets

Get a subset defined by a start row and end row and the step in-between:

>
    start = 10
    step = 37
    stop = 380
    dfSample = df[start:step:stop,:]   

Minor notes:
    - The position of the step is different from Python
    - 'end' is a key word in Julia.

For instance, for very long files, you might want to get an impression of the data by getting some representative data.


## Sort

### Single column

The syntax is very neat.
> 
    df = sort(df, :Cylinders)

For changing the direction of sorting, use the key word **rev**.
>
    df = sort(df, [:Cylinders, :Acceleration], rev=[true, false])


## Create

### Append one new row

New rows need to have the same column structure as the dataframe. 
This leads to a two step process
- create the row with the same types as the dataframe
- append ( = **push** ) it to the existing dataframe

>
    newDate = DateTime(2021,1,1)
    newRow = ["myName", "1", 2, 3, "4", 5, 6, newDate, "Europe"]
    push!(df, newRow)


### Special case

Append a row with the sum of all rows

>
    push!(dfNumbers, sum.(eachcol(dfNumbers)))

Note: 
    - The column type needs to allow the arithmetic operation. You might want separate those columns into a different dataframe.
    - For other operations but sum, you might need to be using Statistics


### Concatenating many rows

For many rows, you should create a new dataframe and concatenate it, rather than appending single rows in a loop.


## Delete

You can delete specific rows using their position.

>
    delete!(df, 100:300)

Delete rows greater than 190

>
    df = df[Not(191:end), :]

