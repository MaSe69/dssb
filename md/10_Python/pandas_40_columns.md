---
layout: 22_python_deep
title: Pandas - Columns
permalink: /pandas_columns

---

# Pandas - Columns

Column operations are the bread and butter of shaping the structure of a dataframe to become more beautiful.

- Rename and Re-order
- Insert and Delete

## Operate only on selected columns

A column is addressed with its name in square brackets directly after the dataframe variable.

>
    df["columnName"]

Alternatively, an existing column with a suitable columnName can be addressed 
>
    df.columnName

Example:
>
    df.colname2 = round(df.colname2, 3)

You can select a subset of columns and apply an operation on it. 

>
    colSel = ["colname1", "colname2"]
    dfcolSel[colSel] = dfcolSel[colSel] * 100.0    

## Rename | Re-order

### Get the column names

In Pandas, what is commonly understood to be the names of the columns, alternatively column names or header, are the values of the columns

>
    columnNames = df.columns.values
    listOfColumnNames = list(df.columns.values)

### Rename columns

You can specify a list of values of your liking and use these new names as the column names.

>
    newColNames = ["Column_1", "Column_2", "Column_3", "Column_4"]
    df.columns = newColNames    


A small piece of beautifying is to have all column names in similar format, e.g. to start with a capital letter.

Capitalize names (or lower, upper, etc.)
>
    columnNames = [x.capitalize() for x in columnNames]    


### Reorder columns

Use the of **existing column names** to re-order the columns, by specifying your sequence
>
    reorderCols = ['Column_2','Column_4','Column_3', 'Column_1']
    df = df[reorderCols]

You can reverse the sequence of the columns as follows
>
    df = df.iloc[:, ::-1]

### Notes

- Mind the correct number of list elements. If you add too many items to the list for the new order, you get an error. However, adding fewer items executes without error.
- Working with indices, e.g.  df = df[:, [2, 1]], does not work in Python (but in Julia)

## Adding Columns

### Append a column at the end

A column can simply be added by specifying a column name that does not exist so far.
We can specify a meaningful default for the month of July in this way.

>
    df["Jul"] = 500

Instead of a fixed value, we could use a random one.
>
    df["Jul"] = random.randint(0, 100)

You can use existing columns to create new ones. 
>
    df["Jul"] = df["Jun"]

On creation, you already can add fixed values. 
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



### Special case

Append a column with the sum of all columns (that are not in the index)
>
    df["Sum"] = df.sum(axis=1)  


## Deleting Columns

You can reduce your table to a table with fewer columns by just specifying the fewer columns that you want to keep.

>
    columnsToKeep = ["Jan","Mar", "May"]
    df = df[columnsToKeep]

Mind the two pairs of square brackets when you enter the values as a one liner.
>
    df = df[["Jan","Mar", "May"]]

You can keep sliced columns
>
    df = df.iloc[:,2:5]


Mostly, keeping the interesting columns is sufficient, but in some cases, it is more efficient to delete or "drop" a few columns.

>
    df = df.drop(["Feb","Apr"], axis="columns")

Alternatively,

> 
    deleteCols = ["Feb","Apr"]
    df = df.drop(deleteCol, axis=1)



