---
layout: 10_topic
title: Pandas
permalink: /pandas_columns

---

In this section, we explore operations on the columns. This includes changing existing columns as well as adding or deleting columns.

## Step 1: Get Column Names, Re-name, Re-order

First of all, you might want to know how the columns are called.
A 'header' is a list of these values of names of the columns.

>
    header = list(df.columns.values)
    print(header)

You can specify a list of values of your liking and use these new names as the column names.

>
    myColumns = ['Account', 'Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun']
    df.columns = myColumns

You can use such a list to re-order the columns.
>
    newOrder =  ['Jan', 'Mar', 'May', 'Feb', 'Apr', 'Jun']
    df = df[newOrder]

{% include images/image.html imagePath = "../images/img_blog/Re-order_Columns.png" imageCaption = "
Our standard table with the longer months to the left."%}

A helpful feature is to reverse the sequence of the columns. 
>
    df = df.iloc[:, ::-1]

This command let the columns start with 'Jun' and ending with 'Jan'.

If you add too many items to the list for the new order, you get an error. However, adding fewer items executes without error.


## Step 2: Keeping or Removing Columns

You can reduce your table to a table with fewer columns by just specifying the fewer columns that you want to keep.

>
    columnsToKeep = ["Jan","Mar", "May"]
    df = df[columnsToKeep]
or
>
    df = df[["Jan","Mar", "May"]]

Mind the two pairs of square brackets when you enter the values as a one liner.

Personally, I favor keeping the requested columns over dropping the other ones. In some cases, it is more efficient thought to delete or "drop" a few columns.

>
    df = df.drop(["Feb","Apr"], axis="columns")

As the drop command works for both columns and rows, you need to specify the axis.

## Step 3: Adding Columns - Operating on Columns

A column can simply be added by specifying a column name that does not exist so far.
We can specify a meaningful default for the month of July in this way.

>
    df["Jul"] = 500

Instead of a fixed value, we could use a random one.
>
    df["Jul"] = random.randint(0, 100)

We can even use the existing columns. We can add a fixed value to such a column or compute manually the average. (Yeah, only for demo purpose)
>
    df["Jul"] = df["Jun"] + 7 
    df["Jul"] = (df["May"] + df["Jun"]) / 2

The principle of working on columns should have become clear.
If you want to work only on a subset of columns, specify that subset and work on it. The remainder of the table remains unchanged.
>
    colSel = ["Jan", "Feb"]
    dfcolSel[colSel] = dfcolSel[colSel] * 100.0

{% include images/image.html imagePath = "../images/img_blog/Added_column.png" imageCaption = "
A column for July added. Jan and Feb multiplied by 100."%}

Another column holding the sum of the complete row can be added.

>
    df.loc[:, 'Total'] = df.sum(axis=1) 

Such a column with totals might be the column most often added to an existing table with currencies.

## Summary

The task was to change the columns of a table.
