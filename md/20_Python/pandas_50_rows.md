---
layout: 20_python
title: Pandas - Rows
permalink: /pandas_rows

---

# Main Operations on Rows

- Get a sub-dataframe
- Sort rows by
    - A single column
    - Multiple columns
- Adding rows
    - Append at the end
    - Append a row with sums
    - Add many rows
- Deleting rows
- Modifying rows

## General comments on rows in Pandas

You can address a row with the (unique) name of its index in square brackets directly after the dataframe variable **and** the key word "loc" - in semantic coding:

>
    df.loc["index"]


Further, you can address a row with its position given as an integer

>
    n = 5
    row = df.iloc[[n]]

## Get a sub-dataframe

Very often used is the function to print out the first few or last few rows. You can also defined new data sets in this way:

>
    dfFirst_7_Rows = df.head(7)

>
    dfLast_7_Rows = df.tail(7)

For very long files, you might want to get an impression of the data by getting some representative data.

>
    start = 10
    end = 80
    k = 37
    rows = df.iloc[start:end:k,:]    

## Sorting

### Single column

The syntax is a bit cumbersome, i.e. one that might need to be looked up again.
It comprises a "sort_values" and - inside the parenthesis - a "by="

> 
    df = df.sort_values(by="column1", ascending=True)


### Multiple columns - in various directions

Certainly, you can also sort by multiple column and in various directions, e.g. 

>
    sortCols = ["column1", "column2"]
    direction =[True, False]
    df = df.sort_values(by=sortCols, ascending=direction)    


## Adding rows
### Append one new row

New rows need to have the same column structure as the dataframe. 
This leads to a two step process
- create the row based on the existing dataframe
- add it to the existing dataframe

>
    columnNames = list(df.columns.values)
    dfNewRows = pd.DataFrame(columns=columnNames)
    dfNewRows.loc[0] = ["myNewCar"] + list((np.random.uniform(20, 80, 3)).round(1))


### Special case

Append a row with the sum of all rows (that are not in the index)

>
    df.loc["Sum"] = df.sum()

### Concatenating many rows

For performance reasons, for instance, for many rows you should create and fill a new dataframe

> 
    dfMultiRows = pd.DataFrame(columns=columnNames)
    for i in range(3):
        dfMultiRows.loc[i] = ['myNewCar' + str(i)] + list((np.random.uniform(20, 80, 3)).round(1))

Concatenate the new dataframe to the existing one. Mind the square brackets for the list. You can concatenate more than two dataframes at once.

>
    df = pd.concat([df, dfMultiRows], axis=0)

Actually, Pandas is 'row-based'. This implies that working on rows is the default. You can, but do not have to, specify 

>
    axis="rows"
    axis=0    

## Deleting rows

You would typically slice the existing dataframe and continue working with the remaining dataframe. Examples:

>
    df = df.loc[df[df.column7] > 17]
    df = df.tail(7)
    df = df.iloc[3:7,:]

However, you can also drop specific rows, e.g. using the index

>
    df = df.drop(df[df.Name == "myNewCar2"].index)

>
    df = df.set_index("Name")
    df = df.drop(index = 'myNewCar1')

Warning: If deletion reduces the Pandas dataframe to just one column, Pandas regards it as a vector. A vector can have different properties, possibly leading to error messages.

## Modifying rows

In fact, cells are changed and technically columns are specified, but it rather feels like changing rows.

### Replace an existing value in a specific column

In an existing row, you can specify the column and replace the value in that row.

>
    df["Name"] = df["Name"].str.replace("myNewCar", "SportsCar")


### Modify column Z based on values in column A

This is a very helpful application for all kind of analysis. 

- Create a new column (with any value)
- Change the value in that column for some rows on condition of values in other columns. 

> 
    df["Environment"] = "NaN"
    df.loc[df['Miles_per_Gallon'] > 20, ['Environment']] = 'Ok'














