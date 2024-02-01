---
layout: 20_python
title: Pandas Read
permalink: /pandas_read
---


# Read Dataframes

The central command to read Pandas dataframes is the function "read", see the [Official Reference on read](https://pandas.pydata.org/docs/reference/api/pandas.read_csv.html) .

>
    pd.read_<file_format>

Though different file formats are supported, here only csv and Excel formats are described.


## Read a dataframe from a csv file

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

You can specify the row in which the column names (or the 'header') is positioned, if they are not in the uppermost row.<br>
Further, you can limit the number of rows to be imported to the dataframe with the parameter 'nrows'. 

>
    df = pd.read_csv(fullPathName, header=17, nrows=4)

You can skip the first n rows or the last m rows

>
    df = pd.read_csv(fullPathName, skiprows=10, skipfooter=11)

Certainly, you can combine most of these parameters, though not all of these combination make sense.


## Read and change values while reading

For the cars dataset, you might want the number of cylinders to be an integer. 

>
    df = pd.read_csv(fullPathName, converters={"Cylinders": int()})

You can define so-called converters, i.e. functions that you include to the read function.

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

Well, a bit meaningless here, just for the sake of demonstration.
