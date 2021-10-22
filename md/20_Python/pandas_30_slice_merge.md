---
layout: 20_python
title: Pandas Slice Merge
permalink: /pandas_slice_merge

---


## Copy

You might want to rename your dataframe or to make a real copy.

>
    df_Diff_Name = df     # Does not create a copy, just adds another name to the existing dataframe
    df_Copy = df.copy()   # Create a real copy 

When you transform a subset of a dataframe, you might better be working on a copy. Changes to df_Copy do not affect df. Without the ".copy()", you change df as well. 

Note that there are two ways to change a dataframe: 
- using the equal sign
- using the parameter "inplace=True"

>
    df = <operate on the df>
    <operate on the df, "inplace=True">

There are quite some reasons to not use the inplace option, see [in-pandas-is-inplace-true-considered-harmful-or-not](
https://stackoverflow.com/questions/45570984/in-pandas-is-inplace-true-considered-harmful-or-not)

 Particularly due to the importance of chaining, only the variant using the equal sign is used here. Unfortunately, this often leads to quite some cumbersome typing effort.

Apart from the index, all cells need to fulfill the prerequesite of the operation.


## Slice

You can reduce an existing dataframe by keeping only a subset of the existing columns.
>
    keepCols = ["Jan","Mar", "May"]
    dfNew = df[keepCols]

Mind the two pairs of square brackets when you enter the values as a one liner.
>
    dfNew = df[["Jan","Mar", "May"]]    

If know the positions of the columns, i.e. the 'integer location', you can also create a new dataframe using iloc
>
    dfNew = df.iloc[:,2:5]    

In general, you can define a 'rectangle' of your dataframe to be a new dataframe - and apply the operation only to that new .

>
    dfSlice = df[r1:r2; c1:c2].copy()

with r1 and r2 being the first and last row, c1 and c2 being the first and last column.

Mind that without the copy your operation might also affect the original dataframe. 


## Merge

Two possibilities are described here:
- concatenate
- merge


### Concatenate Dataframes

You can concatenate dataframes column-wise similarly to row-wise.

As a prerequesite, the rows should reasonably match. If the rows do not match, the second dataframe as appended 'below' the first one, filling many cells with NaN. Usually, this is not what you want.

In many cases, however, the rows do match, e.g. when getting more data on a fixed datetime format and the datetime is in the index. 

>
    df = pd.concat([df1, df2], axis=1)

Mind to specify the axis for the concatenation to be columns.
You can merge more than one dataframe at once.

### Merging on Index or Column Name

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
