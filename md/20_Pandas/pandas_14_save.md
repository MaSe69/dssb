---
layout: 20_python
title: Pandas
permalink: /pandas_save
---


# Save Dataframes

## Save a dataframe to a file in csv format

The command to save a dataframe to a file in csv format is 'to_csv'. 

>
    dfl.to_csv(fileAbsPath, sep=';')

If you do not want comma as delimiter, you need to specify another symbol with the a bit inconsistently parameter 'sep' for separator.


## Save a dataframe to a file in Excel format

Working with the Excel-Format is pretty much the same as working with csv-files.
The 'to_excel' command works similarly as the to_csv command.

>
    dfl.to_excel(writer, sheet_name=sheet)

A few particularities:

- You do not need to specify a deliminator or separator
- You can specify the sheet in Excel to which you want to write the dataframe

