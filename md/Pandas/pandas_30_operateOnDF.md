---
layout: 10_topic
title: Pandas
permalink: /pandas_operateOnDF

---

In this section, we explore operations on the complete tables. This includes operations to describe the table and to modify the table.

In the previous sections, we saw how to

- create tables
- save tables to the file system - and read them again
- plot tables

In the following sections, we will see how to operate

- on columns
- on rows
- on cells

but as for now let's focus on the whole table, i.e. the Pandas dataframe.

As in all section, we follow the paradigm to operate on an 'original' table that we read from the file system before saving the modified table again to the file system.
The sequence is always:

- Read the table from file system. The 'Alpha'-Step.
- Modify the table by applying some operations to it.
- Write the modified table to the file system using another name or even into another folder. The 'Omega'-Step.

Just remember to start with Alpha and to end with Omega.

## Step 1: Rename columns + Set index

The column names of our table saved on the file system originate from the automated creation of time periods.
Such names are unlikely to 'sound nice'. Let's make it a bit more comfortable and give them shorter names that are easier to digest.

We define a list of the same length as the number of columns. Then, we set the columns of the dataframe to that list.

**Coding**
>
    myColumns = ['Account', 'Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun']
    df.columns = myColumns
    df = df.set_index("Account")

Finally, we set the index from the default created by Pandas to the dedicated column.

## Step 2: Local Copy

At first, we should make a local copy of the table that we read from the database. Be aware to make a real copy.

**Coding**
>
    df_New = df.copy()   # Create a copy 
>
    df_New = df          # Does not create a copy, just another name

A new window pops up that contains the plot.

## Step 3: Convert all numerical values

There is no need to convert entries like "123.45" on the csv-file into float.
Sometimes, another type, particularly integers are required.
It might be not enough to get rid of the decimals, which in the scenario here can represent cents, but also to round the integers to larger amounts.

**Coding**
>
    dfInt = dfInt.astype('int32').round(-1)

**Image**
{% include images/image.html imagePath = "../dssb/assets/images/img_blog/opTables_Integers.png" imageCaption = "All values converted to integers and rounded to 10s."%}

## Step 4: Meta data about the dataframe

Often, we just need the number of columns or rows. Using 'shape' is one of several possibilities.

**Coding**
>
    print("Number of (rows, columns):", df.shape)
>
    dfMetaData = df.describe()
    dfMetaData = dfMetaData.astype('int32')

The command 'describe' returns meta data on the dataframe.

**Image**
{% include images/image.html imagePath = "../dssb/assets/images/img_blog/Meta_data.png" imageCaption = "The mean values of the columns and much more statistics."%}

## Step 5: Basic operations on the whole table

Sometimes, all numerical values in a table shall be multiplied with a constant. For instance, we have currency values in Euro, but we need them in Dollar.
Multiplying the dataframe with a constant works. Similarly, a constant value can be added or subtracted.

**Coding**
>
    df = 3.141529 * df

If you wan the decimals, the modulo operator is also available.
>
    df = df % 1

Hence, this notation seems to be as easy as it could be.

## Step 6: Table and Table

If this works for a single value, i.e. a scalar, you might wonder, if it also works for a table.

**Coding**
>
    df = df - df
    df = df / df

We get a table full of zeros or ones, respectively, when subtracting with or dividing by the same table.

### Step 7: Transpose Table

Sometimes, it is of advantage to have the time periods in the rows instead of the columns.
Dataframes can be transposed.

**Coding**
>
    df = df.transpose()

**Image**
{% include images/image.html imagePath = "../dssb/assets/images/img_blog/Table_Transposed.png" imageCaption = "The transposed table has the months as rows."%}

### Out of Scope

You would not compute the inversion of such a table using Pandas, i.e. compute dfI with df * dfI = 1. Instead, use Numpy directly for matrix inversion.

## Summary

The task was to explore the table structure and its content in more detail.

Further, operations that affect the whole table were described here.
