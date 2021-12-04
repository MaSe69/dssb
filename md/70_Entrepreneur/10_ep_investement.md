---
layout: 20_python
title: Beautiful Dataframes
permalink: /ep_margin
---

# Margin Analysis

Let's start with the assumption of an living expense per year of
- 60000 €

A possible investment shall be limited to
- 500000 €

The return needed is the sum of the possible investment and the living expenses. For a given business, realistic margins are often known. Hence, it can be assessed upfront, if a started business will cover living expenses.

Task: Plot the margin as a function of investment. 


## Array

There are many solutions, naturally. 
We start here by creating an array with investment increments. It shall start with 100000 € and the increment by 50000 €.

> 
    incr = 50000
    investArr = []
    for i in range(2, 12):
        invest = i * incr 
        investArr.append(invest)

## Dataframe

Next, we create a dataframe using this array.

>
    df = pd.DataFrame(columns=["Investment"])
    df.Investment = investArr






