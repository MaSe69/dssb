---
layout: 20_python
title: Pandas - Columns
permalink: /pandas_columns

---

# Pandas - Columns

Columns

- [Address](#address-columns)
- [Subsets](#work-on-subsets)
- [Rename](#rename-columns)
- [Reorder](#reorder-columns)
- [Create](#create-columns)
- [Delete](#delete-columns)


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
    
## Work on Subsets

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


## Rename columns


Specify a list of values of your liking and use these new names as the column names.

>
    newColNames = ["Column_1", "Column_2", "Column_3", "Column_4"]
    df.columns = newColNames    


A step in beautification is to convert all column names to a similar format, e.g. to start with a capital letter.

Capitalize names (or lower, upper, etc.)
>
    columnNames = [x.capitalize() for x in columnNames]    


## Reorder Columns

Use the of **existing column names** to re-order the columns, by specifying your sequence
>
    reorderCols = ['Column_2','Column_4','Column_3', 'Column_1']
    df = df[reorderCols]

You can reverse the sequence of the columns as follows
>
    df = df.iloc[:, ::-1]


- Mind the correct number of list elements. If you add too many items to the list for the new order, you get an error. However, adding fewer items executes without error.
- Working with indices, e.g.  df = df[:, [2, 1]], does not work in Python (but in Julia)

## Create Columns

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

Certainly, this is better than to append at the end and then re-order the columns.


# Special 
### Special case

Append a column with the sum of all columns (that are not in the index)
>
    df["Sum"] = df.sum(axis=1)  


## Delete Columns


Delete columns with the drop command:

>
    df = df.drop(["Feb","Apr"], axis="columns")

Alternative notation,

> 
    deleteCols = ["Feb","Apr"]
    df = df.drop(deleteCols, axis=1)


Warning: If deletion reduces the Pandas dataframe to just one column, Pandas regards it as a vector. A vector can have different properties, possibly leading to error messages.

Mind the alternative to continue to work on the relevant subset of columns instead of deleting the obsolete columns.
