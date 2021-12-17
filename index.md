---
layout: 01_landing
title: Beautiful Dataframes
permalink: /index
---
<br>
Dataframes are the focus this [webpage](about).<br>
Dataframes are a corner stone of data science.<br>
Dataframes are popular, because they can store all kinds of tabular data.<br>

Stories can make you to want to be involved. 
Cheat sheets increase your efficiency when being involved.

Python
- [Python - outside dataframes](python_overview) - How to complete tasks that cannot be addressed by dataframes?
- [Using Python Dataframes - Pandas](pandas) - How to create, change, etc. Python dataframes?
- [Altair for Dataframes](altair_overview) - How to plot dataframes in an up-to-date way?
- [Models with Dataframes](models) - How to enhance knowledge about the content of a dataframe? 
- [References on Python Dataframes](python_references) - Which other sources should be used as well?

Julia
- [Julia Dataframes](julia_df) - How to accomplish the same changes to dataframes in Julia?
- [A comparison of Pandas to Julia Dataframes]() - Where are similarities and where are differences?
- [References on Julia Dataframes](julia_references) - Which other sources should be used for Julia as well?

Stories:
- [Dataframes for Entrepreneurs](entrepreneurs) - How to model essential business KPIs using dataframes?
- [Dataframes for Knowledge]() - How to store content knowledge in dataframes?


Great dataframes are not just technical means, but also fulfill criteria of beauty, see [Beautiful Dataframes](beautiful_dataframes)


## Python

All coding here is taken from own working code. Copy&Paste errors may occur.

### Python Outside Dataframes

Some plain Python is definitely needed. Examples:
- Working with Strings, Floats, Arrays, Dictionaries
- Working with comprehensions
- Working with Files

Get an overview on the content, deep dive into coding, find some more details:

- [Overview on Pre-Dataframe Python Usage](python_overview)
- [A listing of helpful Python info](python_listing)
- [Annotations to this Python info](python_annotations)


### Python Dataframes - Pandas

Examples:
- Dataframes: Slice, Subset, Transpose, Concatenate, Merge, ...
- Columns: Create new column, Delete columns, Rename, Re-order, ...
- Rows: Add, Filter, Select, Sort, ...

Get an overview on the content, deep dive into coding, find some more details:

- [Overview on Pandas Usage](pandas).

For getting started, particularly to create dataframes:
- [Listing - Create Pandas Dataframes](listing_pandas).
- [Listing - Work with Pandas Dataframes](listing_pandas_operate).


### Dataframe Visualization - Altair

Examples:
- Charts: Types (Scatter, Line, Area, ...), Size, Titles, ...
- Axis: Labels, Ticks, Scaling
- Complex info: Color, Shape, Trellis, ... 

Get an overview on the content, deep dive into coding, find some more details:

- [Overview on Altair Usage](python_listing).
- [Altair Listing](altair_listing).
- [Altair Listing Annotations](altair_annotations).


After the JuliaCon2021, I migrated my dataframe visualizations in Python from Seaborn to Altair. A main trigger was my experience with the Vegalite.jl package in Julia. Vegalite is based on Vega which in turn is based on the powerful D3 (Data-Driven Documents) library. Altair is the Python equivalent to make use of Vegalite. 

Here is a listing of my usage of Altair to visualize dataframes, including saving charts, using themes, applying time series specifics,

- [Altair About](altair_about).

## Julia Dataframes 

Examples:
- Dataframes: Slice, Subset, Transpose, Concatenate, Merge, ...
- Columns: Create new column, Delete columns, Rename, Re-order, ...
- Rows: Add, Filter, Select, Sort, ...

Get an overview on the content, deep dive into coding, find some more details:

- [Overview on Julia Dataframe Usage](python_listing).
- [Julia Dataframe Listing](pandas_listing).
- [A Julia Overview For Pre-Pandas Usage](python_listing).


# Top Pages

So far in 2021:

- [Pandas Dataframes](pandas)
- [Pandas Columns](pandas_columns)
- [Transpose Julia dataframes](julia_transpose)
- [Julia Columns](julia_columns)
- [Julia Dataframes](julia_df)


### Transpose function in Julia?

Many developers apparently have experienced a surprise when facing the task to transpose a dataframe in Julia. 
Migrating from Python to Julia, you might expect something like df_Transposed = transpose(df), which however does not exist.
In Python, the solution to this problem is as easy as to apply the Pandas transformation T to a dataframe df

>
    df_Transposed = df.T

Find some more details on [Transpose a dataframe in Python](pandas_transpose)

In the discussion, severe problems were pointed out. For a language developer, the problem to transpose a matrix might be remote. Possibly, when you 'own' the data, you can create the dataframe in the way you need it. When you have to combine information from many dataframes from other sources, however, chances are that you need to transpose at least one of them.

>
    You don't need to know all solutions. Just one that works for you.
    