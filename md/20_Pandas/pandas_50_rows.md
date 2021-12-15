---
layout: 20_python
title: Pandas Rows
permalink: /pandas_rows

---

# Pandas - Rows

## Rows - Create

### Append a row at the end

A new row must have the same format as all the other rows which can be achieved by copying an existing row.

>
    df = df.set_index("Name")
    df.loc["MyCar"] = df.loc["ford ranger"].copy()

The new row is the last row in the dataframe.

You can then change any cell value in that row.

>    
    df["Horsepower"]["MyCar"] = 123

The sequence of addressing a cell is [column][row].

### Append a row with the sum of columns

As a special case, you can append a row with the mean 

>    
    df.loc["Mean"] = df.mean()

or the sum of the columns. 
>
    df.loc["Sum"] = df.sum()

When you need both, be careful to not sum up the mean or to include the sum in the average.

In later versions of Pandas, you need to prepare df such that all columns are numeric.

### Insert a new row at a specified position

As a preparation, ensure that the index is reset.
>
    df = df.reset_index()

You can copy any row that exists at a certain position. 
>
    row = df.iloc[27].copy()

And then move the row to the position of your choice. 

>
    df.loc[404] = row

If it shall be the last position, 'shape' can help.
>
    df.loc[df.shape[0]] = row


As before, you can change any field in the row.
>
    df = df.set_index("Name")
    row.Name = "MyCar2"



## Read rows

### Read a row by index

As a preparation, ensure that the index is set to the appropriate field.<br>
Then, you can select the row for this index value.
>
    row = df.loc["audi 100 ls"]

You can also get a cell in that row.
>
    myHorsepower = df.loc["audi 100 ls"]["Horsepower"]    
    myHorsepower = list(df["Horsepower"]["MyCar2"])[0]

The sequence of addressing a cell with 'loc' is [row][column], but without 'loc' is [column][row]. 


### Read rows by position

As a preparation, ensure that the index is reset.
>
    df = df.reset_index()

You can address a row with its position given as an integer
>
    n = 27
    row = df.iloc[n]

If you need the specific position of an index, get it using the function 'index'. 
>
    position = list(df.loc[df.Name == "audi 100 ls"].index)[0]

You can also get a cell in that row.
>
    n = 27
    m = 3
    cell = df.iloc[n][m]    

The sequence of addressing a cell with iloc is [row][column].    


## Slices

### Slice first or last rows

For a set of rows from the beginning the existing dataframe, you can create a new dataframe:

>
    dfFirst_7_Rows = df.head(7)

Respectively, for the last rows    

>
    dfLast_4_Rows = df.tail(4)


### Slice rows by positions and step size

Take a slice between a start row and an end row.

>
    start = 10
    stop = 17
    dfSample = df.iloc[start:stop]  


If you do not want all rows, but just every nth row, add a step size.

>
    start = 10
    stop = 380
    step = 37
    dfSample = df.iloc[start:stop:step]    

For instance, for very long files, you might want to get an impression of the data by getting some representative data.

>
    mySample = df.sample(7)

This is more efficient than to create random integers and take their row positions.

## Rows Update

### Update a specific cell value


You can update a specific cell value using the index and the column name.
>    
    df["Horsepower"]["MyCar2"] = 234    


Alternatively, you can use the integer position with iloc. 

>
    rowPosition = list(df.loc[df.Name == "audi 100 ls"].index)[0]
    colPosition = df.columns.get_loc("Horsepower")

>
    df.iloc[rowPosition][colPositionm] = 78

## Sort

### Single column

The syntax is a bit cumbersome. Don't worry, if you can't memorize.
It comprises **sort_values** and - inside the parenthesis - **by=**

> 
    df = df.sort_values(by="column1", ascending=True)

For changing the direction of sorting, use the key word **ascending**.

>
    sortColumns = ["column1", "column2"]
    direction =[True, False]
    df = df.sort_values(by=sortColumns, ascending=direction)    


## Rows - Delete

### Delete rows by position

You would typically slice the existing dataframe and continue working with the remaining dataframe. Examples:

>
    df = df.loc[df[df.column7] > 17]
    df = df.tail(7)
    df = df.iloc[3:7,:]


### Delete rows by column values

However, you can also drop specific rows, e.g. using the index

>
    df = df.drop(df[df.Name == "myNewCar2"].index)

>
    df = df.set_index("Name")
    df = df.drop(index = 'myNewCar1')
