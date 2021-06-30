---
layout: 10_generic
title: Julia
permalink: /julia_create

---

# Julia - Create Dataframes

Let's start with creating dataframes in Julia.. 

Dataframes are not included in the Julia as such. The full functionality is split to several packages, particularly to minimize the coding you need to import. For a start, the package Dataframes.jl is sufficient.

Installing dataframes in Julia (On the console, enter julia followed by ] ):

>
    add DataFrames.jl


For using Dataframes in a program, declare to be using DataFrames at the top of your program. Mind the capital F.

> 
    using DataFrames


## Start from an Empty Dataframe

It seems to be natural to start with an empty dataframe and then fill it as data becomes available. 

>
    df = DataFrame()

You can add easily columns to the empty dataframe

>
    df = DataFrame(a=1, b=1.0)


Alternatively,
>
    accounts = ["Account_A", "Account_B", "Account_D", "Account_X"]
    df = DataFrame(Accounts=accounts)

Seeing the dataframe growing in this way, i.e. column by column, you certainly figure out quickly how to get to your goal.




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
{% include images/image.html imagePath = "../assets/images/img_blog/Julia/Julia_11_Comparison_DF.png" thisWidth ="400px"%}
Simple dataframe for comparison with Julia dataframe creation.
</center>    

You can create this dataframe as simple as that:

>
    dfPJ = DataFrame(
    Service = service,
    Account = account,
    Quantity = quantity,
    Price = price,
    Cost = cost]

Done.


See here for
- [How to create dataframes in Python](pandas_create)
- [Python vs. Julia comparison for dataframes](python_julia_comparison)


