---
layout: 20_generic
title: Julia
permalink: /julia_createDF

---

# Julia - Create Dataframes Locally

This is kind of 'Hello World' for Dataframes.

It is mainly used to check that the setup is complete and working.
As with most 'Hello Worlds', in real programs, you rarely use it.
Dataframes are usually created when importing data.

The coding used here is available as Jupyter lab: 
[Create_DF.ipynb](https://github.com/MaSe69/dataframes/tree/master/dfJulia)

## Import the package for dataframes

Dataframes are not included in the Julia as such.
The full functionality is split to several packages, particularly to minimize the coding you need to import.

For a start, the pacakge Dataframes.jl is sufficient.

Installing dataframes in Julia:

>
    using Pkg
    Pkg.add("DataFrames")

In order to use Dataframes, you need to import it, which is done by 

> 
    using DataFrames


## A Simple Dataframe

It seems to be natural to start with an empty dataframe and then fill it later.
Such a creation 'from nothing' is possible in Julia. 


>
    df = DataFrame()

You can add easily add columns to the empty data frame

>
    df = DataFrame(a=1, b=1.0)


Alternatively,
>
    accounts = ["Account_A", "Account_B", "Account_D", "Account_X"]
    df = DataFrame(Accounts=accounts)

Seeing the dataframe growing in this way, i.e. column by column, you certainly figure out quickly how to get to your goal.


## Copy of a Dataframe

The default should be and is to keep working on the same technical object representing the dataframe. Sometimes, however, you want to work on a copy, e.g. when transforming a subset of a dataframe.

For Making a real, independent copy of your dataframe use

>
    dfDeepCopy = deepcopy(df)

Changes to dfDeepCopy do not affect df.
Note that 
>
    dfCopy = copy(df)

only makes a "shallow copy" of the dataframe.


## An Example to Compare Dataframes in Python and in Julia

The task shall be to get to a dataframe that looks like this

{% include images/image.html imagePath = "../assets/images/img_blog/createDF_02_Python_Julia_Comparison.PNG" imageCaption =  ""%}

Given are the data as arrays:

>
    service = ["Consulting", "Installation", "Operation"]
    account = ["0815", "1234", "9876"]
    quantity = [10, 100, 50]
    price = [100, 10, 50]
    cost = [30, 7, 25]

You can create this dataframe as simple as that:

>
    df = DataFrame(
        Service = service,
        Account = account,
        Quantity = quantity,
        Price = price,
        Cost = cost
    )

Done.

See here for [the comparison to the same data in a Python dataframe](python_julia_comparison)






