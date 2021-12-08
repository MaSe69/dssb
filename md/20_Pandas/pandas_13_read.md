---
layout: 20_python
title: Pandas
permalink: /pandas_read
---


# Read Dataframes

The central command to read Pandas dataframes is the function "read", see the [Official Reference on read](https://pandas.pydata.org/docs/reference/api/pandas.read_csv.html) .

>
    pd.read_<file_format>

Though different file formats are supported, here only csv and Excel formats are described.


## Read a dataframe from a csv file

You need to specify the name of the full path to the file holding the data and the name of the file including the extension.
After having installed Pandas and imported it, you can read the comma separated data using the command "read_csv".

>
    import pandas as pd
    ...
    fullPathName = <your path> + "cars.csv"
    df = pd.read_csv(fullPathName)

This works for simple file formats right out of the box.
The imported dataframe can be checked, for instance, by looking at the first and last rows.

>
    print(df.head(3))
    print(df.tail(3))

If the columns of your data are not delimited by a comma, but by an other sign, e.g. a semi-colon, then you need to specify this delimiter. 

>
    df = pd.read_csv(fullPathName, delimiter=";")


## Read a dataframe from an Excel file



## Read with conditions on columns

You can restrict the columns imported to those that you really want to use.

>
    colsIwannaUse = ["Name", "Cylinders"]
    df = pd.read_csv(fullPathName, usecols = colsIwannaUse)

Alteratively, you can specify the positions of the columns. 

>
    colsIwannaUse = fullPathName = stem +  "/ZZ_Data/co2.csv"[0, 2, 6]
    df = pd.read_csv(fullPathName, usecols = colsIwannaUse)


## Read with conditions on rows
## Read and change values when reading




## Limiting the data

The 'read_csv' command has many parameters. 
Limiting the amount of data when reading it to local memory is a usually recommended practice in performance.
Though there are special cases when it is better to read everything and throw away the irrelevant parts later.
According to the concept of a beautiful dataframe, you should only have in the dataframe exactly what you want to have.

Let's say, we only want to have two dedicated columns and the first three rows from the 'cars'-data.

>
    colsIwannaUse = ["Name", "Cylinders"]
    df = pd.read_csv(fullPathName, usecols = colsIwannaUse, nrows = 3)


## Tricky raw data

In practice, raw data seldomly comes in the format of your choice.

The delimiter might not be a comma. A comma might be expected to be the default in a comma separated values, but in European notation, decimals are written with a comma, leading to a mess on in a comma separated format.
Further, there might be more 'leading' columns, e.g. having some well-intentioned text.

>
    df = pd.read_csv(fullPathName, delimiter = "|", header=7)
    df.head(3)

Similarly, there is a tail functionality to cut off superfluous data at the end of a file. 

Check the documentation on [read](https://pandas.pydata.org/docs/reference/api/pandas.read_csv.html) for other helpful parameters for your data.

## Converter

If no parameter available, you can still write your own converter. 
Program the functions of your choice. 


>
    def square(x):
        x = int(x)
        return x*x
    def extract(x):
        return x[0:2]

Call them with the syntax of the converter.

>
    df = pd.read_csv(fullPathName, converters={"Cylinders": square, "Horsepower": extract})
    df.head(3)

Well a bit meaningless here, just for the sake of demonstration.


## Timeseries

For timeseries, you can directly read the column holding the date or time into a datetime type.
A datetime can be used, for instance, to add a number of days. 

> 
    df = pd.read_csv(fullPathName, parse_dates=["Date"])
    from datetime import timedelta, date
    df["DatePlus"]= df.Date + timedelta(days=180)
    df.head(10)    


##  Read from an Excel

For working with Microsoft Excel, you need to install a library 
>
    pip3 install xlrd


Reading an external table available in Excel-Format is a common use case.

>
    df = pd.read_excel(fileAbsPath, index_col=0)

## Save to an Excel

Working with the Excel-Format is pretty much the same as working with csv-files.

A few particularities:

- you do not need to specify a deliminator or separator
- you can specify the Sheet in Excel.

