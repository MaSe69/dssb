---
layout: 20_python
title: Pandas Rows
permalink: /pandas_rows24

---

# Pandas - Rows

Because this page turned out to be the most popular on this website on Pandas in the year 2023, I re-worked it in January 2024.
<br>
You might found this page, because you searched for "How to delete the last row of a Pandas dataframe". This is surprising, because this question was already answered in 2014, see ["How to delete the last row of data of a pandas dataframe"](https://stackoverflow.com/questions/26921651/how-to-delete-the-last-row-of-data-of-a-pandas-dataframe). Please find my recommendations on that question at the bottom of this page. 

<br>
Pandas version used to test the example on this page was: 2.2 .
<br>
Let's start with a dataframe that looks like this:

>
        Letter  Occurrences 
    0   A   260
    1   B   31
    2   C   166
    3   Z   6

It comprises how often a letter occurred in the previous version of this page.

The operations are ordered in the CRUD sequence:
- Create
- Read
- Update
- Delete

Slicing is a fundamental technique that can be used in many CRUD operations. I describe the slicing in the context in which I typically use it myself.


# Create rows

## Append a row at the end

A new row must have the same format as all the other rows which can be achieved by copying an existing row.

>
    df = df.set_index("Letter")
    df.loc["X"] = df.loc["Z"].copy()

The new row is the last row in the dataframe. You might now want to update the values in the columns or sort the table (see in the respective section).


### Append a row with the sum of columns

As a special case, you can append a row with the sum of the columns
>
    df.loc["Sum"] = df.sum(numeric_only=True)

You can also have such an additional row with the mean value. When you need both, be careful to not sum up the mean or to include the sum in the average.
In later versions of Pandas, you should add the parameter 'numeric_only'.


## Read rows

'Read' in this context is often known as 'filter'.

### Read a row on condition

You can filter specific row by specifying conditions

>
    df = df.loc[df.Letter == "C"]
    df = df[df.Occurrences > 100]

As a result, you get a dataframe that is reduced to the rows meeting the condition.

### Read rows by index

You can also access a row using the index. 
>
    position = list(df.loc[df.Letter == "C"].index)[0]
    row = df.iloc[position] 

As a result here, you get a series.


# Update Rows

## Update a specific cell value

Any cell value can be updated using 'at'. The first entry in the list is the index. Hence, I set the index to "Letter" first.
>
    df = df.set_index("Letter")
    df.at["C","Occurrences"] = 17


## Slices

### Slice first or last rows

You can use 'head' or 'tail'. 

>
    dfFirst_7_Rows = df.head(7)
    dfLast_4_Rows = df.tail(4)

You can get a random sample
>    
    dfRandom_3Rows = df.sample(3)

Be aware that it is not sorted like the underlying dataframe.


### Slice rows by positions and step size

Take a slice between a start row and an end row with a step size in-between.

>
    start = 1
    stop = 5
    step = 2
    dfPart = df.iloc[start:stop:step]    


## Sort

### Sort the rows of a dataframe by columns

You can sort It comprises **sort_values** and - inside the parenthesis - **by=**

> 
    df = df.sort_values(by="Letter", ascending=True)

    

### Sort by several columns in mixed directions

For changing the direction of sorting, use the key word **ascending**.

>
    sortColumns = ["column1", "column2"]
    directions = [True, False]
    df = df.sort_values(by=sortColumns, ascending=directions)    

The sequence of the column names in the list needs to match, of course.


# Delete rows

## Delete rows on condition

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


### Delete rows by keeping other columns

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





