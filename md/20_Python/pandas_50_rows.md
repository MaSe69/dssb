---
layout: 20_python
title: Pandas Rows
permalink: /pandas_rows

---

# Pandas - Rows

Rows

- [Address](#address-rows)
- [Subsets](#work-on-subsets)
- [Sort](#sort)
- [Create](#create-rows)
- [Delete](#delete-rows)


## Address Rows

Address a row with the (unique) name of its index in square brackets directly after the dataframe variable **and** the key word "loc" - in semantic coding:

>
    df.loc["index"]


Further, you can address a row with its position given as an integer

>
    n = 5
    row = df.iloc[[n]]

## Work on Subsets

### First or Last Rows

For a bulk of rows from the begining or the end of the existing dataframe, you can create a new dataframe:

>
    dfFirst_7_Rows = df.head(7)

>
    dfLast_7_Rows = df.tail(7)


### Generic Subsets

Get a deliberately defined subset using iloc:

>
    start = 10
    end = 80
    k = 37
    rows = df.iloc[start:end:k,:]    

For instance, for very long files, you might want to get an impression of the data by getting some representative data.
## Sort

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


## Create Rows
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

## Delete rows

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













