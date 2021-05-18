---
layout: 10_topic
title: Pandas
permalink: /pandas_createDF

---

# Pandas

## Create dataframes



## Table From Arrays


We want to create a table with accounts and months. All values shall be 0.
Let's put the months as columns and accounts as rows.

- At first, we create a list for the accounts.
- Second, a list for the months. 
- Third, we use the pandas command to create the dataframe using the accounts as index and the months as columns.
- Finally, we fill the values of the cells with zeros.

**Coding**
>
    accounts = ["Account_A", "Account_B", "Account_D", "Account_X"]
    months = ["January", "February", "March"]
    df = pd.DataFrame(index=accounts, columns=months)
    df = df.fillna(0)


As intended, the output is a table.

**Output**
>
                January  February  March
    Account_A        0         0      0
    Account_B        0         0      0
    Account_D        0         0      0
    Account_X        0         0      0


This completes the first part.
In summary, we created a simple table realized as a Pandas dataframe.

## Step 2: Make the columns more dynamic

In the next step, we want to achieve flexibility on the number of rows.
We started with months, but the time period could also be days or weeks or else.
Specifying the number of a columns to a table should of course be flexible.

Using pandas’ period_range, the start, the increment and the repetition can be easily defined. Setting the "frequency" to "M", we stick with months, but could easily change to days, quarters, years or other time periods.


**Coding**
>
    months = pd.period_range(start="2020-01-01", periods=8, freq="M")

Then, the cell values should reflect values in a currency. Random numbers with 2 digits - representing currency values - would be nice.
This can be achieved as follows:

**Coding**
>
    cellValues = np.random.rand(4, 8) * 1000
    cellValues = cellValues.astype(float).round(2)
    df = pd.DataFrame(cellValues, index=accounts, columns=months)

Now the result looks much more like an real-life accounting table.

**Output**
>
               2020-01  2020-02  2020-03  2020-04  2020-05  2020-06  2020-07  2020-08
    Account_A   351.16   982.01   241.13   422.12   499.90   721.31   525.59    59.76
    Account_B   690.57    82.52   194.08    54.63   460.64   901.15   303.77   699.62
    Account_D   555.01   591.41   825.60   403.47   856.62   485.57   716.13   602.52
    Account_X   506.24   197.62   912.49   717.87   988.16   585.67   957.28   112.60

 In summary, we extended the table to a flexible number of columns for time periods.

## Step 3: Define a Function for Table Creation

The Pandas syntax to create dataframes or to create a list for time periods is quite special in the sense that you might have to look it up every time you use it. You might want to wrap this syntax hence in your personal programming style.

In a professional program you also should not repeat coding, but reuse or refine existing one. As we know now how to create a table, let's wrap it to create many, many more tables.

Re-use is typically done by defining a function. Functions need to be defined before they are called. Hence, we have to deal with this function first.

- The column should represent any time interval, e.g. days, weeks, months, years, and certainly should start at any time to cover as many iterations as we like.
- The number of accounts should also be flexible and determined by the number of accounts that we provide in the list.

Function have parameters. Providing the required mandatory input parameters can be painful, because it requires all interfaces to be adapted at the same time to avoid syntax errors. 

Luckily, a single parameter, when defined as a dictionary, can do the trick in Python. Let's call that general purpose parameter for short ‘para’. The local data frame shall be called "dfl".


**The Function**
>
    def pdDFFromListsCreate(para):
        dfl = pd.DataFrame(para["CellValues"], index=para["Index"], columns=para["Columns"])
        return dfl

**Parameters for the columns**
>
    para["StartDate"] = "2020-06-01"
    para["TimeInterval"] = "D"
    para["NrColumns"] = 6
    para["Columns"] = pd.period_range(
        start=para["StartDate"], periods=para["NrColumns"], freq=para["TimeInterval"]
    )


**Parameters for the rows**

>
    accounts = ["Account_A", "Account_B", "Account_D", "Account_F", "Account_X"]
    para["Index"] = accounts
    para["NrRows"] = len(accounts)

**Parameters for the values**

>
    cellValues = np.random.rand(para["NrRows"], para["NrColumns"]) * 1000
    cellValues = cellValues.astype(float).round(2)
    para["CellValues"] = cellValues

The output is a table with six days as columns and with an additional row. 

**Output**
>
               2020-06-01  2020-06-02  2020-06-03  2020-06-04  2020-06-05  2020-06-06
    Account_A      496.62      578.81      730.94      697.60      967.98       64.05
    Account_B      177.26      942.11      604.33      103.91      513.84      455.17
    Account_D       32.24      629.63      442.73      916.11      827.24      314.53
    Account_F      444.54      298.93       39.16      600.06      674.27      175.03
    Account_X      792.80      289.78      189.62      560.98      407.42      468.28


In summary, we can call a function in any program that returns a table with a specified number of time periods, accounts and some random values in the rows.

### Create an Empty Pandas Dataframe - Not Really Possible

It seems to be natural to start with an empty dataframe and then fill it later. 

This assumptoin is backed by a highly voted question on Stackoverflow: [Creating an empty pandas dataframe - then filling it](
https://stackoverflow.com/questions/13784192/creating-an-empty-pandas-dataframe-then-filling-it).

As a workaround you can fill the cells with random numbers which are replaced with the real entries later.

## Summary and conclusion

It is easy to create tables as dataframes in Pandas.

The task was to create meaningful tables to be used for testing in professional programs.
This is an entry point to a full-scale data science.





