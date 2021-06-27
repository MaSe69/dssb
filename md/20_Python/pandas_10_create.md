---
layout: 20_python
title: Pandas
permalink: /pandas_create
---

# Python - Create Dataframes

Let's start with creating dataframes in Python using Pandas. 

First of all, you need to download the library Pandas 

>
    pip3 install pandas

and to import Pandas at the top of your program.

> 
    import pandas as pd



## Create an Empty Dataframe

It seems to be natural to start with an empty dataframe and then fill it as data becomes available. 

>
    df = pd.DataFrame()

For getting a print out of the result, 
- in Jupyter, you need to add a line to get the print out
- in Visual Studio Code (VSC), you need to print the dataframe to the console

>
    df          ### Jupyter
    print(df)   ### Coding


Fill the dataframe column by column.

>
    df["Col_C1"] = [11, 12]
    df["Col_C2"] = [21, 22]

Fill the dataframe row by row.

>
    df = pd.DataFrame(columns=["Col_R1", "Col_R2"])
    df.loc["Col_R1"] = [11, 12]
    df.loc["Col_R2"] = [21, 22]

But do not loop over dataframes! As it is correctly pointed out in a highly voted question on Stackoverflow: [Creating an empty pandas dataframe - then filling it](
https://stackoverflow.com/questions/13784192/creating-an-empty-pandas-dataframe-then-filling-it), though you can create and fill dataframes by looping over data, particularly for performance reasons, you should not do so. Get your data first into an efficient structure, e.g. lists, then create the (final) dataframe.


## A Simple Dataframe

Getting started, we create a table with accounts and months. All values shall be 0.
Let's put the months as columns and accounts as rows.

- At first, we create a list for the accounts.
- Second, a list for the months. 
- Third, we use the pandas command to create the dataframe using the accounts as index and the months as columns.
- Finally, we fill the values of the cells with zeros.

You should be able to copy and paste the coding below. It should run, using the import statement above.

>
    accounts = ["Account_A", "Account_B", "Account_D", "Account_X"]
    months = ["January", "February", "March"]
    df = pd.DataFrame(index=accounts, columns=months)
    df = df.fillna(0)


Your result should be similar to:

<center>
<br>
{% include images/image.html imagePath = "../assets/images/img_blog/createDF_01_First_Dataframe.PNG" thisWidth ="600px"%}
</center>

Certainly, though technically a dataframe, this is just mere 'list' or 'table', still a bit away from a 'beautiful dataframe'.

Dataframes can be created in an elegant way from a dict.

>
    pd.DataFrame.from_dict(myDict)

In practice, however, this is found to be rarely needed. 


## An Example to Compare Dataframes in Python and in Julia

Task: Put these arrays as columns to a dataframe with the capitalized array name as column name. 

>
    service = ["Consulting", "Installation", "Operation"]
    account = ["0815", "1234", "9876"]
    quantity = [10, 100, 50]
    price = [100, 10, 50]
    cost = [30, 7, 25]

<center>
<br>
{% include images/image.html imagePath = "../assets/images/img_blog/Python/Pandas_11_Comparison_DF.png"  thisWidth =600px%}
Simple dataframe for comparison with Julia dataframe creation.
</center>

One (of many) solutions is to create a dataframe using the rows as they are given in the task

>
    rows = [service, account, quantity, price, cost]

Then, create a dataframe based on these rows. I called it "dfPJ" abbreviating "dataframe for Python Julia comparison".
>    
    dfPJ = pd.DataFrame(data=rows)

Transpose the dataframe
>
    dfPJ = dfPJ.T

Rename the columns
>
    colNames = ["Service", "Account", "Quantity", "Price", "Cost"]
    dfPJ.columns = colNames

Stay tuned for the introduction on transpose dataframes and renaming columns.


See here for
- [How to create dataframes in Julia](julia_create)
- [Python vs. Julia comparison for dataframes](python_julia_comparison)
