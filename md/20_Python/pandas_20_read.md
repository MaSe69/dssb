---
layout: 20_python
title: Pandas
permalink: /pandas_read
---


# Read Dataframes

The central command to read data frames is simply the [read](https://pandas.pydata.org/docs/reference/api/pandas.read_csv.html) function
>
    pd.read_<file_format>

There are many file formats, e.g. excel, json. However, here we stick to csv. 

One of the most time consuming issues in practice might be to re-find the files.
This issues can be left to 'data governance' and is outside the scope here.
It might be considered a good idea to *not* store* the data in the same folder as the coding, but in a separate folder.

>
    filename = "../Data/cars.csv"
    df = pd.read_csv(filename)
    df.head(3)

 

## Limiting the data

The 'read_csv' command has many parameters. 
Limiting the amount of data when reading it to local memory is a usually recommended practice in performance.
Though there are special cases when it is better to read everything and throw away the irrelevant parts later.
According to the concept of a beautiful dataframe, you should only have in the dataframe exactly what you want to have.

Let's say, we only want to have two dedicated columns and the first three rows from the 'cars'-data.

>
    colsIwannaUse = ["Name", "Cylinders"]
    df = pd.read_csv(filename, usecols = colsIwannaUse, nrows = 3)
    df    


## Tricky raw data

In practice, raw data seldomly comes in the format of our choice.

The delimiter might not be a comma. A comma might be expected to be the default in a comma separated values, but in European notation, decimals are written with a comma, leading to a mess on in a comma separated format.
Further, there might be more 'leading' columns, e.g. having some well-intentioned text.

>
    df = pd.read_csv(filename, delimiter = "|", header=7)
    df.head(3)

Similarly, there is a tail functionality to cut off superflous data at the end of a file. 

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
    df = pd.read_csv(filename, converters={"Cylinders": square, "Horsepower": extract})
    df.head(3)

Well a bit meaningless here, just for the sake of demonstration.


## Timeseries

For timeseries, you can directly read the column holding the date or time into a datetime type.
A datetime can be used, for instance, to add a number of days. 

> 
    df = pd.read_csv(filename, parse_dates=["Date"])
    from datetime import timedelta, date
    df["DatePlus"]= df.Date + timedelta(days=180)
    df.head(10)    

# Save dataframes

Saving locally is much easier.
Being in the dataframe, the data are already in a convinient format.


The central command to save dataframes in csv-format is simply the [to_csv](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.to_csv.html) function

Some thoughts though:
- Think about a convinient name to save the file. Mind to not accidently overwrite the original file.
- Do not save the index, you might end up with two indices after re-reading the file again.
- Mind that some people have good reason for not using comma as the delimiter.

>
    df.to_csv('filenameSave', index=False, delimiter=";")

