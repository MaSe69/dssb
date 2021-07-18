---
layout: 20_python
title: Pandas Group
permalink: /pandas_group

---

# Group

## Group and Combine

You can aggregate numerical values in one column for identical values in another column

For instance, for the cars dataset, you can first group for the year and the origin.

> 
    df = df.groupby(["Year", "Origin")

Then, you can combine to get the average weight for each grouping

>
    df = df.Weight_in_lbs.mean()

This is part of the so-called Split-Apply-Combine (SAC) pattern.

The steps above can be combined to 

>
    df = df.groupby(["Year", "Origin"]).mean()

This results in an index holding the year and the origin, and all other columns being averaged.


