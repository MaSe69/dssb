---
layout: 20_python
title: Pandas - Merge
permalink: /pandas_merge

---


# Merging Different Dataframes Column-wise

We limit ourselves here to columns, because adding dataframes by rows has already been treated in the rows section.

Two possibilities are described here:
- concatenate
- merge

## Concatenate Dataframes

You can concatenate dataframes column-wise similiarly to row-wise.

As a prerequesite, the rows should reasonably match. If the rows do not match, the second dataframe as appended 'below' the first one, filling many cells with NaN. Usually, this is not what you want.

In many cases, however, the rows do match, e.g. when getting more data on a fixed dateime format and the datetime is in the index. 

>
    df = pd.concat([df1, df2], axis=1)

Mind to specify the axis for the concatenation to be columns.
You can merge more than one dataframe at once.

## Merging Dataframes

If concatenation is not an option, merge usually is sufficient.
Merging is limited to two dataframes at a time, a 'left' dataframe and a 'right' dataframe.

A standard way to get to a successful merge is to move the common column to the index. In case of issues, check both index fields to be of the same type.

You can then specify to merge on the index of the 'left' and the 'right' dataframe.

>
    df = pd.merge(df1, df2, how="outer", left_index=True, right_index=True)

For the kind of merge, there are several options in for the 'how' parameter. As subsequent results might very decisively depend on the type of merge, you might want to check in depth to have taken the appropriate way of merging.

Instead of taking the index, you can save some coding and directly merge on columns that are semantically identical, i.e. they even can have different names. Just to give an example from existing coding: 
>
    dfMerged = pd.merge(df1, df2, how="left", left_on=para["KeyLeft"], right_on=para["KeyRight"])


## Conclusion

Merging dataframes together with splitting, in particular, slicing, them, provides you with the tools to transform a dataframe semantically to exactly the shape that you want it to be.


