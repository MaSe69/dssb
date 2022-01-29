---
layout: 01_landing
title: Beautiful Dataframes
permalink: /index
---
<br>
Dataframes are [popular](df_popularity).<br>
Dataframes are essential to [data science]().<br>
Dataframes are at the main thing what this webpage is [about](about).<br>


## Topics and Stories

Many might notice dataframes only as a tool that helps on some topics. 

- [Explorative Data Analysis](altair_story) - Starting with the Vega cars, introducing themes, exploring Altair interactivity, advancing to multi selection.
- [Time series](time_series_story) - Data of a year are used to predict data of the next year leading to Logistics regression.
- [Categorization](cat_story) - Data are clustered and the clusters visualized.


### Explorative Data Analysis Using Pandas and Altair

The chart below shows the static version of an interactive chart in which the legend can be used to select one or multiple items. Because this landing page should remain neat and fast, the interactive version and the explanation is on a separate page. Just click on the image to go there and you find the interactive chart.

<br>
<center>
<a href="vega_cars_multi_selection">
{% include images/image.html imagePath = "../assets/images/img_blog/img_altair/vegacars_i_multiselect.png" imageCaption =  ""%}
</a>
<br><b>
This chart uses the 'standard' cars example provided by Vega and commonly used for introductions.
</b><br>
</center>
<br>

 Dataframe operations were used to work on the original data, e.g. European units are used here. <br>
 You notice that all charts here look similar, because they share the same theme.

Start here with this [Explorative Data Analysis](vega_cars).


### Time Series, Regression and Interaction

A common use case is to predict this year's data from last years data. <br>
Once such a prediction was made, you might want to point out clearly the deviation of new value from the prediction. 

<br>
<center>
<a href="time_series_tooltip">
{% include images/image.html imagePath = "../assets/images/img_blog/img_altair/TooltipForRegressionStatic.png" imageCaption =  ""%}
</a>
<br><b>
You see here the actual value and the predicted value. 
</b><br>
</center>
<br>


 Start here with this [Time Series Analysis](time_series_starter).

### Categorization

First, there need to be categories, which might be retrieved from data. 
A so-called model is then often used to assign test data to such categories.

<br>
<center>
<a href="time_series_tooltip">
{% include images/image.html imagePath = "../assets/images/img_blog/Python/BDF/30_BDF_CAT/alt_09_C_iris_kmeans.png" imageCaption =  ""%}
</a>
<br><b>
A standard example for classification.
</b><br>
</center>
<br>

Start here with this [Categorization Analysis](cat_story).



# Dataframes in Python

What was needed to complete the stories above should be described here.<br>
Though it might look like a lot, it's only a tiny fraction of what is available.<br>
If you don't find here, what you are looking for, you might want to deep dive here: [References on Python Dataframes](python_references) 


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

##  Visualization of Dataframe in Python

The content of a dataframe is usually clear to the person who has worked for it. Often, this content needs to be presented which is mostly done using visualization.

Altair is a Python visualization that has a great interface to dataframes.<br> 
Altair enables interactive charts. Click on the chart below or on the following link to get to the [interactive version for multiple selection](vega_cars_multi_selection). 



You can get here a brief [Altair overview](altair_overview).<br>
You can find details directly in the [Altair listing](altair_listing).<br>

The content on visualization is grouped into 3 categories.<br>

- Charts: Types (Scatter, Line, Area, ...), Size, Titles, ...
- Axis: Labels, Ticks, Scaling, ...
- Interactivity: Tooltips, Selections, ...


##  Cheat Sheets - Python - Summary

- [Python - outside dataframes](python_overview) - How to complete tasks that cannot be addressed by dataframes?
- [Create Python Dataframes - Pandas](listing_pandas) - How to get to Python dataframes?
- [Work with Python Dataframes - Pandas](listing_pandas_operate) - How to create, read, update, delete (CRUD) dataframes, columns, rows?
- [Altair for Dataframes](altair_listing) - How to plot dataframes in an up-to-date way?


# Dataframes in Julia

Dataframes are available in both Python and Julia. They share similarities, but they are not equal. 

- [Julia Dataframes](julia_df) - How work on dataframes in Julia?

Examples:
- Dataframes: Slice, Subset, Transpose, Concatenate, Merge, ...
- Columns: Create new column, Delete columns, Rename, Re-order, ...
- Rows: Add, Filter, Select, Sort, ...

Find here [a comparison between Pandas and Julia Dataframes]().

- [References on Julia Dataframes](julia_references) - Which other sources should be used for Julia as well?

Great dataframes are not just technical means, but also fulfill criteria of beauty, see [Beautiful Dataframes](beautiful_dataframes)


# Top Pages

In 2021:

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

If this all here is too long to read and seems to be too complex, remember that somebody said:

>
    "You don't need to know all solutions. Just one that works for you."
    