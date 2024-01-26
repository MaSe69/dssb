---
layout: 20_python
title: Pandas Rows
permalink: /pandas_rows24

---

# Pandas - Rows

Because this page turned out to be the most popular on this website on Pandas in the year 2023, I partly re-wrote it. Please find the previous page here [Pandas Rows - Previous Version](pandas_rows).
<br>
Surpringlingly, there were so many searchs on "How to delete the last row of a Pandas dataframe", though this question was already answered in 2014, see ["How to delete the last row of data of a pandas dataframe"](https://stackoverflow.com/questions/26921651/how-to-delete-the-last-row-of-data-of-a-pandas-dataframe). Please find my summary on that question at the bottom of this page. 

Let's start with a dataframe that looks like this:

>
        Letter  Occurrences 
    0   A   260
    1   B   31
    2   C   166
    3   Z   6




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

### Read a cell by columns and index    

You can also get any cell in that row when you specify the column name and the index.
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

### Sort by a column

The syntax is a bit cumbersome. Don't worry, if you can't memorize.
It comprises **sort_values** and - inside the parenthesis - **by=**

> 
    df = df.sort_values(by="column1", ascending=True)

### Sort by several columns in mixed directions

For changing the direction of sorting, use the key word **ascending**.

>
    sortColumns = ["column1", "column2"]
    directions = [True, False]
    df = df.sort_values(by=sortColumns, ascending=directions)    

The sequence of the column names in the list needs to match, of course.


## Rows - Delete

### Delete rows on condition

You can drop specific rows using the index. <br>
When you know the index of the row by name, you can directly delete (=drop) that row.

>
    df = df.set_index("Name")
    df = df.drop(df[df.Name == "myNewCar2"].index)

Certainly, you can specify conditions.
>    
    dfS = dfS.drop(dfS[dfS.index.isin(['mazda rx-4'])].index)
    dfS = dfS.drop(dfS[dfS.index.str.contains('dodge')].index)    

Certainly, you can specify conditions, e.g. on the index.
>    
    dfS = dfS.drop(dfS[dfS.index.isin(['mazda rx-4'])].index)
    dfS = dfS.drop(dfS[dfS.index.str.contains('dodge')].index)    

The condition can apply on any other field.
>
    dfS = dfS.drop(dfS[dfS.Cylinders == 8].index)
    dfS = dfS.drop(dfS[dfS.Cylinders.isin([4, 6, 8])].index)


### Remove rows by keeping other columns

As an alternative to deletion, you can slice the existing dataframe on a condition. 
If you have a condition for the rows that you want to keep, you use this condition to remove the other rows.

>
    dfS = dfS.loc[dfS["Cylinders"] != 4]

The same result as above using the index can be achieved by keeping the inverse of the 'positive condition'.
>
    dfS = dfS.loc[~dfS["Cylinders"].isin([4,6,8])]

Mind the tilde "~" that inverses the condition. In terms of performance, this might not be the optimal solution though.

As a reminder, you can also use positions to keep some rows and thereby removing the other rows.
>    
    df = df.tail(7)
    df = df.iloc[3:7,:]


### Delete the last row or rows of a Pandas dataframe

There are several possibilities listed here in sorted descendingly in my favor, but they all worked for me.

>
    ### Slice
    df = df[:-1]
    df = df.iloc[:-1,:]

>
    ### Drop with index
    df = df.drop(df.index[-1])

>
    ### Drop with index (alternative)
    lastIndex = len(df)-1
    df = df.drop([lastIndex])

(Be aware that Python starts with 0, hence the index is one less than the length)





