---
layout: 10_topic
title: Pandas - Rows
permalink: /pandas_rows

---

# Operations on Rows

In this section, we explore operations on the rows. This includes adding, sorting and deleting (filtering) rows in a table of fixed column sructure.

## Step 1: Add rows

First of all, you might want to know how the columns are called.
A 'header' is a list of these values of names of the columns.

>
    header = list(df.columns.values)
    print(header)
