---
layout: 10_topic
title: Pandas
permalink: /pandas_createDF

---
# Create Dataframes Locally

This is kind of 'Hello World' for Dataframes.

It is mainly used to check that the setup is complete and working.
As with most 'Hello Worlds', in real programs, you rarely use it.
Dataframes are usually created when importing data.

The coding used here is avaialbe as Jupyter lab: 
[Create_DF.ipynb](https://github.com/MaSe69/dataframes/blob/master/dfPython/PY_11_Create_DF.ipynb)


## Import Pandas

Using Pandas, it certainly has to be imported.

> 
    import pandas as pd


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


For getting a print out of the result, 
- in Jupyter, you need to add a line to get the print out
- in coding, e.g in Visual Studio Code (VSC), you can print it out to the console

>
    df          ### Jupyter
    print(df)   ### Coding

Your result should be similar to:

{% include images/image.html imagePath = "../assets/images/img_blog/createDF_01_First_Dataframe.PNG" imageCaption =  ""%}

Certainly, though technically a dataframe, this is just mere 'list' or 'table', still a bit away from a 'beautiful dataframe'.

## Reference of Copy of a Dataframe

The default should be and is to keep working on the same technical object representing the dataframe.
Sometimes, however, you want to work on a copy, e.g. when transforming a subset of a dataframe.

Make a copy of your dataframe using

>
    dfCopy = df.copy()

Changes to dfCopy do not affect df. Without the ".copy()", you change df as well. 

Note that there are two ways to change a dataframe: 
- using the equal sign
- using the parameter "inplace=True"

>
    df = <operate on the df>
    <operate on the df, "inplace=True">

There are quite some reasons to not use the inplace option, see [in-pandas-is-inplace-true-considered-harmful-or-not](
https://stackoverflow.com/questions/45570984/in-pandas-is-inplace-true-considered-harmful-or-not)

Here, only the assignment variant is used, particularly due to the importance of chaining. Unfortunately, this often leads to quite some cumbersome typing effort.


## An Example to Compare Dataframe in Python and in Julia

>
    service = ["Consulting", "Installation", "Operation"]
    account = ["0815", "1234", "9876"]
    quantity = [10, 100, 50]
    price = [100, 10, 50]
    cost = [30, 7, 25]


## Not Possible - Create an Empty Dataframe

It seems to be natural to start with an empty dataframe and then fill it later. 

This assumptoin is backed by a highly voted question on Stackoverflow: [Creating an empty pandas dataframe - then filling it](
https://stackoverflow.com/questions/13784192/creating-an-empty-pandas-dataframe-then-filling-it).

As a workaround, as indicated, you can fill the cells with NaN, zeros or random numbers which are replaced with the real entries later.






