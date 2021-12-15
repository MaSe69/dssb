---
layout: 20_python
title: Pandas Columns
permalink: /pandas_columns

---

# Pandas - Columns

## Create columns

### Append new column to the end

A new column can be created by simply add its column name in square brackets and quotation marks after its dataframe variable. 

In the cars example, Europeans might prefer the weight being measured in kilograms. A new column called "Weight_KG" holds the values of the existing column Weight_in_lbs divided by the respective conversion number.

>
    df["Weight_KG"] = df.Weight_in_lbs / 2.20462

Mind:
- A new column cannot be addressed by df.newColumn, it needs to be df["newColumn"].
- A new column created in this way is appended at the end.

#### Append a column with a numerical index

Sometimes, the dataframe has no numerical index, but you need one, e.g. for a merge. Maybe, the numerical index should start with 1, e.g. for counting months.

>
    df["A_Numberical_Column"] = range(1, df.shape[0]+1)

You can create a column with random integers.

>
    import numpy as np
    df["Random_Number"] = np.random.randint(0, 100, size=df.shape[0])


Some of the previous examples with obvious meaning.

>
    df["Jul"] = df["Jun"] * 1.19
    df["Jul"] = (df["May"] + df["Jun"]) / 2


You can also use the name of the operations, e.g. add, subtract, multiply or divide. 
If the two columns that you need are distributed in two dataframes, df1 and df2 say, then you still perform the operation.

>
    df1["Ratio"] = df1[["Weight_in_lbs"]].divide(df2["Acceleration"], axis=0)

You do not need to merge dataframes first. 


### Append a new column B based on values in existing column A

You can create a new column and immediately set values dependent on values in another column.

In the cars example, we add a column 'Region' and set it according to the value in the column 'Origin'. As a preparation, we create a dictionary that holds the mapping between the existing and the new values.

>
    newValues = {"United States": "America", "Europe": "Europe", "Japan": "Asia"}
    for key, value in newValues.items():
        dfS.loc[dfS["Origin"].str.contains(key, na=False), "Region"] = value


### Append a column with the sum of other columns

Provided all columns are numerical and the index is set, you can append a column holding the sum of each row. 

>
    df["Sum"] = df.sum(axis=1) 

Pushing it a bit further, you can append another column holding the sum of these sums.
>
    df["CumSum"] = df.Sum.cumsum() 


### Insert new column at a specified position

For columns that should go to a specific position, you can directly insert a new column at a position.

>
    colPosition = 3
    df.insert(colPosition, column='columns3', value=df.column1 * 0.7457)

This is more efficient than to append at the end and then re-order the columns.


## Read Columns

Read an existing column with its name in square brackets and quotes directly after the dataframe variable.

>
    df["myColName"]

Alternatively, an existing column with a suitable columnName can be addressed 
>
    df.myColName

Specifying the column, you can perform basic operations.
>
    df.Acceleration = df.Acceleration" / 17


###  Read column names

In a format efficient for further processing, you can get the column names.

>
    colNames = list(df.columns.values)

For instance, you can print the column names and copy&paste them to your program.


### Select and keep a subset of columns

You can select ( or read or filter) a subset of the existing columns using an array of column names.
For instance, you can print specified columns

>
    print(df[["Name", "Weight_KG", "Consumption_lper100km", "Origin"]])

### Select a subset of columns

You can select column names by position using an array of existing names.
Alternatively, you can select column names by position using iloc
>
    dfS = df.iloc[:,2:7]
    dfS = df.iloc[:,[0,1,3,6]]

The figures are the positions of the columns. Certainly, you can compute them dynamically, if the position is not known at design time.

### Keep a subset of columns

Often people keep working on a too large dataframe, because they do not know how to reduce it. 
You should keep the columns that you really need and copy them to a new dataframe.

>
    keepCols = ["Name", "Weight_KG", "Consumption_lper100km", "Origin"]
    dfS = df[keepCols].copy()

Mind the two brackets [["Name", "Origin"]] needed, when you put the column names directly after df.


### Rename columns

Rename specific single columns.

>
    df = df.rename(columns={'Weight_KG':'Weight_EU', 'Sum':'Total'})


Rename all columns, by specifying a list of unique values

>
    newColNames = ["Column_1", "Column_2", "Column_3", "Column_4"]
    df.columns = newColNames    

A dataframe is more beautiful, when all column names are in the same format, e.g. all start with a capital letter. Capitalize names (or lower, upper, etc.)
>
    columnNames = [x.capitalize() for x in columnNames]    


### Reorder existing columns

Use the of **existing column names** to re-order the columns, by specifying your sequence
>
    reorderCols = ['Name', 'Year', "Horsepower", 'Origin']
    df = df[reorderCols]

- Mind the correct number of list elements. If you add too many items to the list for the new order, you get an error. However, adding fewer items executes without error.
- Working with indices, e.g.  df = df[:, [2, 1]], does not work in Python (but in Julia)

As a special case, you can reverse the sequence of the columns.
>
    df = df.iloc[:, ::-1]


## Update cells of a column

### Convert the type of a column

Round floats to 2 decimals.
>
    df["Ratio"] = round(df["Ratio"],2)

 Convert floats to integers
 >
    df["Ratio"] = round(df["Ratio"],0).astype(int)  

Reading dates from a file, some date formats are automatically converted to an integer. This can be fixed by this conversion.

 >
    df["Date"] = df["Date"].astype(str) 

These are really often used conversions.


### Update some numerical values

You update (or change) the value for a complete column by just setting a new value.

>
    df["Random_Number"] = random.randint(0,100)
    df["Name"] = "Just a car - doesn't matter which one."

More commonly, you need to update the values in a column for specific rows. 
You can do this change like in a normal matrix notation. Also, the notation with ".loc" before the row does work.

>
    df["Random_Number"]["chevy s-10"] = 77
    df["Random_Number"].loc["chevy s-10"] = 78

The sequence is [column][row].

You can also change values using the position of the column and the rows.
First, you need to find out the index position(s) that you want to change.
>
    thisIndex = list(df.loc[df.Name == "chevy s-10"].index)[0]

You can do the update using the column notation and just replace the 'loc' with the 'iloc' and the name of the row in the index with the position of the index.

>
    df.Random_Number.iloc[thisIndex] = 79

Finally, you can also replace the column with the position.
>
    df.iloc[thisIndex:thisIndex+1, 12:13] = 80

Mind that in this case 
- the notation is [rowLower:rowUpper,columnLower:columnUpper]. 
- the upper boundary must be set appropriately.


### Update some String values

You update (or change) the value for a complete column by just setting a new value.


Select a column of type String and replace the value in each row for a specified condition.

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

## Delete columns

### Delete columns by name

Delete columns with the drop command:

>
    dfS = dfS.drop(["Weight_EU","Consumption_EU"], axis='columns')

Alternative notation,

> 
    deleteCols = ["Weight_EU","Consumption_EU"]
    df = df.drop(deleteCols, axis=1)


Warning: If deletion reduces the Pandas dataframe to just one column, Pandas regards it as a vector. A vector can have different properties, possibly leading to error messages.


### Delete columns by positions

Just specify the position of the columns.
>
    dfS = dfS.drop(dfS.columns[2:4], axis=1)

Mind Python beginning with 0 and mind the index.

### Delete last column

For instance, if you appended a column for the sum, but want to remove this column again before you plot the original columns.

>
    dfS = dfS.drop(dfS.columns[dfS.shape[1]-1], axis=1)

Mind the alternative to deleting columns by filtering for the columns that you want to continue with.

For a big number of columns, you can proceed as follows:
- Move the columns to a list
- Shorten that list by filtering for the columns that you want to keep, e.g. by applying a comprehension to that list.
- Keep the columns in the short list.
