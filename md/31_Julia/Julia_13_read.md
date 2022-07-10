---
layout: 30_julia
title: Julia Read
permalink: /julia_read

---

# Read

Using package "CSV", you can use

- CSV.read, or
- CSV.File

to create a dataframe from a csv-file. You need to add the CSV package and then to declare its usage

>
    using CSV


You find here only info on csv-files. Certainly, Julia offers to create dataframes from a multitude of other file formats, including JSON, Excel, etc. .

In any case, you need to specify the source, which can be done as follows

>
    filename = "cars.csv"
    path = "./ZZ_Data/"
    relname = path * filename
    println(relname)

You can check, if filename in the console output leads to the correct csv-file.


## CSV.read

Closer to the Python command is the read command. 
- You need to specify the data type into which the csv-file shall be converts, which is in this case of course **DataFrame**. 
- If you stored the csv-file with a different delimiter than the default comma, you need to specify this delimiter when reading. 
- See the [Documentation on read](https://csv.juliadata.org/stable/) for further parameters.

>
    df = CSV.read(relname, DataFrame, delim=";")

You might want to limit the print out of a long dataframe to the first rows. You can check the type, if it is really a dataframe.

>
    println(first(df,4))
    println(typeof(df))


## CSV.File

Instead of the read command, you can also use the File command of the CSV package. 

Then, you need to frame the result into a dataframe.

>
    df = DataFrame(CSV.File(relname))


Alternatively, you  can pipe the result into a dataframe. 

>
    df2 = CSV.File(relname) |> DataFrame

This way comes natural, when you are chaining a lot of pipes anyway.


## Limiting the data

Limit the number of rows read from the csv-file, by setting a **limit**.

>
    df = CSV.read(relname, DataFrame, limit=3)



You can limit the number of columns. <br>
Using **select**, you can specify the column names.

>
    df = CSV.read(relname, DataFrame, select=[:Horsepower, :Cylinders])

Alternatively, you can specify the column number.

>
    df = CSV.read(relname, DataFrame, select=[1, 3])


## Tricky raw data


Other parameters that proved helpful for reading real world data were:
- header
- skipto
- footerskip
- transpose
- comment
- ignoreemptylines
- decimal


## Timeseries

For using dates, you need to add the package ("Dates") and declare its usage.
>
    using Dates

Use **dateformat** to specify the format, in which the date is held in the csv-file.
For the co2-example used on this site,

>
    filename = "co2.csv"
    path = "./ZZ_Data/"
    relname = path * filename

the first part of timeseries can be read as follows:

>
    myDateFormat="yyyy-mm-dd"
    df = CSV.read(relname, DataFrame, dateformat="$myDateFormat", limit=3)

The column 'Date' is then of type **date**.

