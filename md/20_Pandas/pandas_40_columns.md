---
layout: 20_python
title: Pandas Columns
permalink: /pandas_columns

---

# Pandas - Columns

Columns

- [Address](#address-columns)
- [Basic Arithmetics On Columns](#Basic-arithmetics-on-columns)
- [Rename](#rename)
- [Reorder](#reorder)
- [Insert](#insert)
- [Modify](#modify)
- [Delete](#delete)


## Address Columns

Address an existing column with its name in square brackets and quotes directly after the dataframe variable.

>
    df["myColName"]

Alternatively, an existing column with a suitable columnName can be addressed 
>
    df.myColName


If you do not know the column names, get their names

>
    columnNames = df.columns.values
    listOfColumnNames = list(df.columns.values)


## Basic Arithmetics On Columns

Often, you cannot apply an operation on the complete dataframe, but only a set of selected rows. 
Alternatively, you can create a new dataframe with the specified columns and merge the result back later.

### Multiplying with a scalar

For scalars, just use the normal symbols: 
>
    df.Acceleration = df.Acceleration" / 17
    df["Acceleration"] = df["Acceleration"] / 17

Select a subset of columns and apply an operation on it. 

>
    selectedColumns = ["colname1", "colname2"]
    df[selectedColumns] = df[selectedColumns] * 100.0    


You can also use the name of the operations, e.g. add, subtract, multiply or divide. 

>
    df["Ratio"] = df[["Weight_in_lbs"]].divide(df["Acceleration"], axis=0)


### Multiply a column with a column to get an additional column

Particularly, multiplying two columns to yield a third one in the same dataframe.

>
    df2.C. = df2.A + df2.B
    df2[C] = df2[A] * df2[B]

The result here is an additional column with column name C that is the row-wise product of columns A and B.

Such column-with-column-multiplications have a lot of practical use cases.


### Converting a type

Often used, round floats or convert floats to integers
>
    df["Ratio"] = round(df["Ratio"],2)
    df["Ratio"] = round(df["Ratio"],0).astype(int)  


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


### Check for uniqueness


First, you might want to check, if a column has only unique values. You can code a condition, or just print out the Boolean value

>
    print(dfU.Name.is_unique)

which happens to be False in this case. Here, dfU shall be a copy of the cars dataframe.

### Count non-unique values in columns

Additionally, you might want to know how many of the total number of entries are unique.

>
    numberUniqueNames = dfU.Name.nunique()

If you need a percentage of non-uniqueness, you get the total number of entries using
>
    numberNames = dfU.Name.count()

Further, you might want to select those non-unique values. First, create a column that holds the Boolean value for uniqueness, then select for this Boolean value.

>
    dfU["MyDuplicates"] = dfU.Name.duplicated()
    dfDup = dfU.loc[dfU.MyDuplicates == True]

This is just one solution of possibly many.    

### Keep unique values by dropping duplicates

Typically, you want to remove the non-unique values to just keep one copy of the value and thus making the column unique. You do this when you drop the duplicates.

>
    dfU = dfU.drop_duplicates(subset=["Name"], keep='first')

You can choose, if you want to keep the first or the last value.

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
