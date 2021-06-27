---
layout: 20_python
title: Pandas Columns
permalink: /pandas_columns

---

# Pandas - Columns

Columns

- [Address](#address-columns)
- [Change Numerical Values](#change-numerical-values)
- [Subsets](#work-on-subsets)
- [Rename](#rename-columns)
- [Reorder](#reorder-columns)
- [Create](#create-columns)
- [Delete](#delete-columns)
- [Modify](#modify-columns)


## Address Columns

Address an existing column with its name in square brackets and quotes directly after the dataframe variable.

>
    df["myColName"]

Alternatively, an existing column with a suitable columnName can be addressed 
>
    df.myColName

More Examples:

>
    df.myColName2 = round(df.myColName, 3)


If you do not know the column names, get their names

>
    columnNames = df.columns.values
    listOfColumnNames = list(df.columns.values)

### Change Numerical Values

For scalars, just use the normal symbols: 

>
    df["Acceleration"] = df["Acceleration"] / 17

For columns, use the methods, e.g. add, subtract, multiply or divide, 

>
    df["Ratio"] = df[["Weight_in_lbs"]].divide(df["Acceleration"], axis=0)    


Round floats or convert floats to integers
>
    df["Ratio"] = round(df["Ratio"],2)
    df["Ratio"] = round(df["Ratio"],0).astype(int)  

    
### Work on Subsets

Select a subset of columns and apply an operation on it. 

>
    colSel = ["colname1", "colname2"]
    dfcolSel[colSel] = dfcolSel[colSel] * 100.0    

Create a new dataframe with a subset of existing columns.

>
    keepCols = ["Jan","Mar", "May"]
    dfNew = df[keepCols]

Mind the two pairs of square brackets when you enter the values as a one liner.
>
    dfNew = df[["Jan","Mar", "May"]]

Create a new dataframe using sliced columns
>
    dfNew = df.iloc[:,2:5]


## Rename


Rename specific single columns, e.g. A to Alpha and B to Beta:

>
    df = df.rename(columns={'A':'Alpha', 'B':'Beta'})


Rename all columns, by specifying a list of unique values

>
    newColNames = ["Column_1", "Column_2", "Column_3", "Column_4"]
    df.columns = newColNames    


A step in beautification is to convert all column names to a similar format, e.g. to start with a capital letter.

Capitalize names (or lower, upper, etc.)
>
    columnNames = [x.capitalize() for x in columnNames]    


## Reorder 

Use the of **existing column names** to re-order the columns, by specifying your sequence
>
    reorderCols = ['Column_2','Column_4','Column_3', 'Column_1']
    df = df[reorderCols]

You can reverse the sequence of the columns as follows
>
    df = df.iloc[:, ::-1]


- Mind the correct number of list elements. If you add too many items to the list for the new order, you get an error. However, adding fewer items executes without error.
- Working with indices, e.g.  df = df[:, [2, 1]], does not work in Python (but in Julia)

## Insert

### Add a column at the end

Specify a unique name in square brackets and quotes.

>
    df["June"] = 500
    df["July"] = random.randint(0, 100)

You can use existing columns to create new ones. 
>
    df["Jul"] = df["Jun"]

More complex computations are possible.

>
    df["Jul"] = df["Jun"] * 1.19
    df["Jul"] = (df["May"] + df["Jun"]) / 2

### Insert a new column at specific position

For columns that should go to a specific position, you can directly insert a new column at a position.

>
    colPosition = 3
    df.insert(colPosition, column='columns3', value=df.column1 * 0.7457)

This is more efficient than to append at the end and then re-order the columns.


## Special 

### Special case

Append a column with the sum of all columns (that are not in the index)
>
    df["Sum"] = df.sum(axis=1)  


## Delete


Delete columns with the drop command:

>
    df = df.drop(["Feb","Apr"], axis="columns")

Alternative notation,

> 
    deleteCols = ["Feb","Apr"]
    df = df.drop(deleteCols, axis=1)


Warning: If deletion reduces the Pandas dataframe to just one column, Pandas regards it as a vector. A vector can have different properties, possibly leading to error messages.

Mind the alternative to continue to work on the relevant subset of columns instead of deleting the obsolete columns.


## Modify

### Replace an existing value in a specific column

Name the column and replace the value in a row for a specified condition

>
    df["Name"] = df["Name"].str.replace("myNewCar", "SportsCar")


### Modify column B based on values in column A

Change the value in a column, here 'Environment', for some rows on condition of values in another column, here 'Miles_per_Gallon' 

> 
    df.loc[df['Miles_per_Gallon'] > 20, ['Environment']] = 'Ok'


All cars with more than 20 miles per gallon get the ok here.

### Create a new column B based on values in column A

Create a new column with values specified in a dictionary before.

>
    newValues = {"Consulting": "Cons", "Installation": "Inst", "Operation": "Ops"}
    for key, value in newValues.items():
        df.loc[df["Service"].str.contains(key, na=False), "Abbreviation"] = value

A new column with abbreviations was created.

