---
layout: 10_topic
title: Pandas
permalink: /pandas_saveDF

---

# Save and read dataframes

Previously, we created some tables. Now it is time to save them.

We only save to the file system. A database is not needed at this stage.
Much further down the road there comes a point in time when adding functionality would become equal to rewriting a database.
Then, it is worth considering to use an existing database.

Here we handle, for a table in dataframe format

- Write to a csv-file
- Read from a csv-file
- Write as a Excel
- Read from Excel

As we need to save to a folder, we should get the absolute path of that folder.
Python returns to us the current path, which is shall be called "stem" here. Using this stem, we don't have to worry in which programming environment we are.

**Coding**
>
    para["Stem"] = os.getcwd()

Based on this stem, we can define a path relative in our programming environment.

Finally, we need a filename. The filename itself can be separated into a "basename" and an "extension". The extension varies here depending, if we want to write to a csv-file or to an Excel. Keeping the extension undefined, it can be set by the called function. In this way, the file can be written without further code modification to several formats.

## Step 1: Save to a CSV-File

Choosing the separator is one of the freedoms we have on the csv-format. Working with comma and points on currencies, it is more advisable to work with a different separator, e.g. the semicolon ";".

**Coding**
>
    para["Path"] = "/Blog_Data/"
    para["Basename"] = "Accounts"
    para["Delimiter"] = ";"

Given these parameters, the function call can be made to write the file in csv-format to the file system.

**Coding**
>
    fileAbsPath = para["Stem"] + para["Path"] + para["Basename"] + ".csv"
    df.to_csv(fileAbsPath, sep= para["Delimiter"], encoding="utf-8")

As a result, we find a new csv-file created on the file system.

**Image**
{% include images/image.html imagePath = "../dssb/assets/images/img_blog/Accounts.png" imageCaption =  "Table saved as csv-file."%}

## Step 2: Read from a CSV-File

This tool certainly opens up the possibility to read tables into Pandas dataframes.
As can be expected, the commands are quite similar.

**Coding**
>
    fileAbsPath = para["Stem"] + para["Path"] + para["Basename"] + ".csv"
    df = pd.read_csv(
        fileAbsPath, sep=para["Delimiter"], 
        header=0, index_col=0, skipinitialspace=True
    )

Because it might be boring to read exactly the file that was written before, let's make use of having random numbers in each table. Running the write program with the basename "Accounts_previous" gives us a 'previous version of this table' on the file system, when the program is executed once more. Hence, the current table, which is written to the file system has different value from that one read from the file system.

At the end of this program, we have two tables, Accounts.csv and Accounts_Previous.csv, at runtime and on the file system.
Both tables have the same column names and row names, but different cell values.

## Step 3: Save to an Excel

Working with the Excel-Format is pretty much the same as working with csv-files.

A few particularities:

- we do not need to specify a deliminator or separator
- we can specify the Sheet in Excel.

**Image**
{% include images/image.html imagePath = "../dssb/assets/images/img_blog/Accounts_as_Excel.png" imageCaption =  "Table saved in Excel-Format but displayed with LibreCalc."%}

## Step 4: Read from an Excel

Last, but not least, we want to read from an Excel.
Reading an external table available in Excel-Format might be the most common use case.

**Coding**
>
    df = pd.read_excel(fileAbsPath, index_col=0)

Before reading the table, I edited the first column to make it more plausible that it was edited in between saving and reading.

**Image**
{% include images/image.html imagePath = "../dssb/assets/images/img_blog/Excel_as_read.png" imageCaption =  "Table as read from Excel-Formatted file."%}

## Summary

The task was to save and read tables created with Pandas dataframes to the file system.
We saved by using both the csv-format and the Excel-format.
