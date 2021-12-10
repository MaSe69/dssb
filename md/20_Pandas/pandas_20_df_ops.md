---
layout: 20_python
title: Pandas DF Ops
permalink: /pandas_df_ops

---

# Operations on the Dataframe

Here are some selected operations on the entire dataframe.

## Meta data about the dataframe

First, let's get some info about the dataframe, i.e. the so-called meta data.

### Get number of rows

The function 'shape' - to be used without parenthesis - returns the number of columns or rows. 

>
    nrRows = df.shape[0]
    print("Number of rows:", nrRows)

### Get number of columns

Get the number of columns with the second element of shape. 

>
    nrColumns = df.shape[1]


### Get data types of columns

The data type of each column is listed with 'dtypes'

>
    myDataTypes = df.dtypes

### Get some statistics on the dataframe content

The function 'describe' - to be used with parenthesis - returns some statistics on the numerical values of the dataframe.

>
    someStatistics = df.describe()



## Application to all cells


### Set Index

A particularity of Pandas is the index. The index is always the first column of the dataframe. If the table has only one column, this first column is generated automatically. 

If you set an existing column as index, this generated column vanishes. It reappears, though, when you reset your index. 
Any columns can be set as index.

>
    df = df.set_index("Name")

You reset the index like this.

>
    df = df.reset_index()


### Transpose dataframe

In Python, there is a transpose operator 'T'. 

>
    dfT = df.T

In the transposed dataframe, the element [i,j] in df is at [j,i] in the transposed dataframe dfT.<br>
When there is an automatically created index, i.e. 0, 1, 2, ... , it will be moved to the column names. Usually, this is not wanted, so set the index first to the requested new header.
In the cars, this would mean:

> 
    df = df.set_index("Name")
    dfT = df.T

As a result, the names of the cars, which were in the rows of the first column, are in the column names.

### Fill all missing values

Some dataframes contain only numerical values, except maybe for the index.
Then, it can be efficient to set all missing values to zero.

>
    df = df.fillna(0)


### Round all floats

Some dataframes contain only floats.
Then, it can be efficient to round all floats to the same number of digits. For currencies, that would be two digits.

>
    df = df.round(2)

For converting the integers, you might chain the commands.

>
    df = df.round(0).astype(int)


### Multiply with a value

Provided, all cells (outside the index) are numeric, they can simultaneously be added, subtracted, multiplied or divided by a value (= a scalar).

>
    df = df + 1
    df = df - 1
    df = df * 17
    df = df / 18

## From wide format to long format and vice versa

As preparation, let's reduce the cars dataframe to a few columns and remove duplicates from the column 'Name'. 

>
    keepCols = ["Name", "Horsepower", "Cylinders"]
    dfW = df[keepCols].copy()
    dfW = dfW.drop_duplicates(subset=['Name'], keep='last')

### Convert from wide to long format

The long format is commonly needed in the Altair charts. For instance, for a scatter plot that shows horsepower per car, but the different number of cylinders shall be visualized as well. 

You need to specify the column that holds the unique keys. Here, we take the column 'Name', after having removed duplicates. You can choose deliberately the column names for the columns holding the variables and the values.

> 
    dfL = dfW.melt(id_vars="Name", var_name="Variable", value_name="Value")


### Convert from long to wide format

The long format can be converted back to the wide format using the function 'pivot'. The index needs to be the unique key. The different values in the column 'Variable' are used to create new columns. The values are 'distributed' to these columns.

>
    dfW = dfL.pivot(index='Name', columns='Variable', values='Value')

As a result, we get essentially the same dataframe as before melting it from wide to long format.



### Split apply combine

The split apply combine (SAC) pattern is essentially carried out using the group command.

You might want to start with a copy of the original dataframe
>
    dfG = dfRaw.copy()

Specify one or more column names for which you want to do the grouping
>
    groupFields = ["Origin", "Year"]
    dfG = dfG.groupby(groupFields).mean()

The first columns of dfG now contain the fields for which you grouped. 


## Concatenate or Merge Dataframes

### Vertically concatenate dataframes 

As a preparation, let's spit the cars dataframe into one holding only cars from the USA and another one holding only cars from Europe.

>
    dfUS = df.loc[df.Origin == "USA"]
    dfEU = df.loc[df.Origin == "Europe"]

These two dataframes can be joined or concatenated again to look like the original dataframe (except for the missing other cars)

>
    dfWest = pd.concat([dfUS, dfEU])

Mind that the dataframes must be in an array. For vertical concatenation, i.e. along the rows, the direction does not need to be specified, because this direction is the default.

### Horizontally concatenate dataframes 


As a preparation, let's spit the cars dataframe into a left-hand part and a right-hand part. Before the split, let's set the column 'Name' as the index, such that it is kept in both dataframes as the index. Further, let's drop the two non-numeric columns.

>
    df = df.set_index("Name")
    df = df.drop(["Origin", "Year"], axis=1)
    df1 = df.iloc[:,:4]
    df2 = df.iloc[:,4:]

The horizontal concatenation is technically very similar to the vertical concatenation, except that the direction along the columns must be specified with 'axis=1' or axis='columns'.

>
    dfCon = pd.concat([df1, df2], axis=1)

The result is essentially identical the the original dataframe df.


### Merge dataframes

In this case identical to the horizontal concatenation, but generally more powerful, is the function 'merge'. 
>
    dfMer = pd.merge(df1, df2, how="inner", on="Name")

The third parameter specifies the logic with which the two dataframes are merged. Depending on this parameter, the outcome can be drastically different. Another very useful option than merging on the same name of a column is to merge on the index.


### Add another dataframe

Two dataframes of identical shapes and containing numerical values can be added or subtracted. 

>
    df = df1 + df2

In the example above, it be checked, if the concatenation and the merge resulted in the same dataframe, i.e. the result ideally should be a dataframes with zeros in all cells.

>
    print(dfCon - dfMer)
