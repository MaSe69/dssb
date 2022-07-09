---
layout: 01_landing
title: Beautiful Dataframes
permalink: /index
---



This is a web site on some Data Science topics.<br>
You are welcome to browse through the many charts - ideally you will find something of your interest.<br>
If you are a programmer, most of the coding is provided on pages linked below.<br>


# Some Data Science in Python

- [Fundamentals](fundamentals) - Covering some Python, some Pandas, some Altair and some Dash.
- [Time series](time_series_story) - Leading to to Logistics regression using Pandas, Altair, Dash.
- [Categorization](cat_story) - Covering some Machine Learning Algorithms.


## Fundamentals

This is a result after having completed the 'fundamentals section' here. 
It shows data of the 'cars' in the Vega dataset. It is a screenshot of the interactive version.

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

Click on the graph to find the interactive version of it.

Continue on [Fundamentals](fundamentals) ... 


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
    