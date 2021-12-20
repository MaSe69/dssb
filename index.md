---
layout: 01_landing
title: Beautiful Dataframes
permalink: /index
---
<br>
Dataframes are [popular](df_popularity).<br>
Dataframes are essential to [data science]().<br>
Dataframes are at the main topic of this [webpage](about).<br>

You might want to get involved when reading fascinating [stories](#stories).<br>
You increase your imagination and efficiency substantially when using [cheat sheets]().


## Python

### Python (Plain)

Some plain [Python](python_overview)  is definitely needed, for instance to work with
- Arrays, Dictionaries, Comprehensions
- Flow logic
- Files



### Python Dataframes - Pandas

First, you need to [get your dataframes](listing_pandas). There are several methods described.

Then, you might want to [work on dataframes](listing_pandas_operate). This is a deep topic.<br>

The content here on working with dataframes is grouped into 3 categories.<br>

- Dataframes: ..., slice, merge, ...
- Columns: Create new columns, Rename, Re-order, ... , Delete columns
- Rows: Create new rows, Filter, Select, Sort, ..., Delete rows

It is further grouped according to CRUD (Create, Read, Update, Delete)

### Python Dataframe Visualization

After having worked on your dataframe, you might want to visualize some of its content using [Altair](altair_overview).<br>

The content on visualization is grouped into 3 categories.<br>

- Charts: Types (Scatter, Line, Area, ...), Size, Titles, ...
- Axis: Labels, Ticks, Scaling
- Complex info: Color, Shape, Trellis, ... 

Get an overview on the content, deep dive into coding, find some more details:


### Python Dataframes and Models

Missing data might be approximated by models and added to the dataframe.<br>
An interesting model is the Logistic function, see [Models with Dataframes](models) 


## Link list on Python:

- [Python - outside dataframes](python_overview) - How to complete tasks that cannot be addressed by dataframes?
- [Using Python Dataframes - Pandas](pandas) - How to create, change, etc. Python dataframes?
- [Altair for Dataframes](altair_overview) - How to plot dataframes in an up-to-date way?
- [Models with Dataframes](models) - How to enhance knowledge about the content of a dataframe? 
- [References on Python Dataframes](python_references) - Which other sources should be used as well?


## Julia Dataframes 

Dataframes are available in both Python and Julia. They share similarities, but they are not equal. 

- [Julia Dataframes](julia_df) - How work on dataframes in Julia?

Examples:
- Dataframes: Slice, Subset, Transpose, Concatenate, Merge, ...
- Columns: Create new column, Delete columns, Rename, Re-order, ...
- Rows: Add, Filter, Select, Sort, ...

Find here [a comparison between Pandas and Julia Dataframes]().

- [References on Julia Dataframes](julia_references) - Which other sources should be used for Julia as well?

### Stories

- Get started with dataframes and their [visualization](altair_story)
- Use dataframes for [time series](time_series_story)
- Use dataframes as an entrepreneurs to [model a potential business](entrepreneurs) - 


Great dataframes are not just technical means, but also fulfill criteria of beauty, see [Beautiful Dataframes](beautiful_dataframes)


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

## Finally

>
    "You don't need to know all solutions. Just one that works for you."
    