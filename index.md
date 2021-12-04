---
layout: 01_landing
title: Beautiful Dataframes
permalink: /index
---
<br>
Dataframes are the focus this webpage.<br>
Dataframes are a corner stone of data science.<br>
Dataframes are popular, because they can store all kinds of tabular data.<br>

Stories can make you to want to be involved, listings of knowledge (as above) empower you to get involved.
Stories:
- [Dataframes for Entrepreneurs]() - How to model essential business KPIs using dataframes?
- [Dataframes for Knowledge]() - How to store content knowledge in dataframes?

Python
- [Python - outside dataframes]() - How to complete tasks that cannot be addressed by dataframes?
- [Pandas - Working on Python Dataframes]() - How to create, change, etc. Python dataframes?
- [Altair for Dataframes]() - How to plot dataframes in an up-to-date way?
- [Models with Dataframes](models) - How to enhance knowledge about the content of a dataframe? 
- [References on Python Dataframes](python_references) - Which other sources should be used as well?

Julia
- [Julia Dataframes](julia) - How to accomplish the same changes to dataframes in Julia?
- [A comparison of Pandas to Julia Dataframes]() - Where are similarities and where are differences?
- [References on Julia Dataframes](julia_references) - Which other sources should be used for Julia as well?


Finally, 
- [Thoughts on 'beauty of dataframes']()

## Python

### Python Outside Dataframes

Some plain Python is definitely needed. Examples:
- Working with Strings, Floats, Arrays, Dictionaries
- Working with comprehensions
- Working with Files

- [Overview on Pre-Dataframe Python Usage](python_overview).
- [A listing of helpful Python info](python_listing).
- [Annotations to this Python info](python_annotations).


### Python Dataframes - Pandas

Examples:
- Dataframes: Slice, Transpose, Concatenate, Merge, ...
- Columns: Add, Delete, Rename, Re-order, ...
- Rows: Add, Filter, Sort, ...

- [Overview on Pandas Usage](python_listing).
- [Pandas Listing](pandas_listing).
- [Pandas Listing Annotations](pandas_annotations).


### Dataframe Visualization - Altair

Examples:
- Charts: Types (Scatter, Line, Area, ...), Size, Titles, ...
- Axis: Labels, Ticks, Scaling
- Complex info: Color, Shape, Trellis, ... 

- [Overview on Altair Usage](python_listing).
- [Altair Listing](altair_listing).
- [Altair Listing Annotations](altair_annotations).


After the JuliaCon2021, I migrated my dataframe visualizations in Python from Seaborn to Altair. A main trigger was my experience with the Vegalite.jl package in Julia. Vegalite is based on Vega which in turn is based on the powerful D3 (Data-Driven Documents) library. Altair is the Python equivalent to make use of Vegalite. 

Here is a listing of my usage of Altair to visualize dataframes, including saving charts, using themes, applying time series specifics,

- [Altair About](altair_about).

## Julia Dataframes 

Examples:
- Dataframes: Slice, Transpose, Concatenate, Merge, ...
- Columns: Add, Delete, Rename, Re-order, ...
- Rows: Add, Filter, Sort, ...

- [Overview on Julia Dataframe Usage](python_listing).
- [Julia Dataframe Listing](pandas_listing).
- [A Julia Overview For Pre-Pandas Usage](python_listing).


# Top 3 Pages 2021

- [Transpose Julia dataframes](julia_transpose))
- [Julia dataframes](julia_)
- [Pandas Columns](pandas_columns)


## Special topic: Transpose a dataframe in Julia or Python

In Python, the solution to this problem is as easy as to apply the Pandas transformation T to a dataframe df

>
    df_Transposed = df.T

Find some more details on [Transpose a dataframe in Python](pandas_transpose)

In Julia, however, there is no equivalent like df_Transposed = transpose(df).
In the discussion, severe problems were pointed out. The usual workaround is to extract a matrix and to rebuild the dataframe, as I pointed out here: [Transpose a dataframe in Julia](julia_df_ops#transpose).
For many cases, these hints might be sufficient to struggle on and to end up with a transposed dataframe.

For a language developer, the problem to transpose a matrix might be remote. Possibly, when you 'own' the data, you can create the dataframe in the way you need it.
When you have to combine information from many dataframes from other sources, however, chances are that you need to transpose at least one of them.

### Transpose a dataframe in Julia

Find here, how to
[Transpose a dataframe in Julia](julia_transpose)

