---
layout: 20_python
title: Julia DF Slice Merge
permalink: /julia_slice_merge

---

# Operations on the Entire Dataframe

Here are some selected operations on the entire dataframe.


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


