---
layout: 30_julia
title: Julia DF Groups
permalink: /julia_group
---

# Group

## Group and Combine

You can aggregate numerical values in one column for identical values in another column

For instance, for the cars dataset, you can first group for the year and the origin.

> 
    df = groupby(df, [:Year, :Origin])

Then, you can combine to get the average weight for each grouping

>
    df = combine(df, :Weight_in_lbs => mean)

This is part of the so-called Split-Apply-Combine (SAC) pattern.


