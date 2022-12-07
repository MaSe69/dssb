---
layout: 01_landing
title: Beautiful Dataframes
permalink: /index
---


This is a web site on some Data Science topics.<br>
It includes content that I taught during an academic course on 'Data science in Python' in 2022 leading to a bachelor degree.<br>

Update (December 2022):<br>
Preparing for the repetition of this course, I am working on new versions of some content.
For regular users of this page, I try not to delete content. Though, if there is a better version, it will replace the existing one.<br>

Some preview on changes:
- A new [refresher on 'Python for Pandas'](python_refresher).
- Focus on Plotly for graphs and dashboards.
- Work mostly on a single data set, i.e. the Scottish first forenames.


# Some Data Science in Python

The topics covered here are:

- [Fundamentals](fundamentals) - Python, Pandas, and several visualization libraries for Data Science.
- [Time Series](time_series_overview) - Leading to to Logistics regression using Pandas, Altair, Dash.
- [Categorization](cat_story) - Covering some Machine Learning Algorithms on discrete variables.


## Fundamentals

This is a result after having completed the 'fundamentals section' here. <br>
The cars data of the Vega Dataset are often used for teaching.
The data have been prepared using the Python library 'Pandas'.
The visualization was done using Altair.

<br>
<center>
<a href="vega_cars_multi_selection">
{% include images/image.html imagePath = "../assets/images/img_blog/mainpage22/Main22_Vega_Cars.png" imageCaption =  ""%}
</a>
<br><b>
The chart above shows data of the 'cars' dataset of Vega. This is a screenshot of the interactive version to which you can go when clicking on it.
 </b><br>
</center>
<br>

A dashboard created with the same data.<br>
When selecting the number of cylinders in the drop down box, only the respective data are shown. The second graph shows the average fuel consumption.

<br>
<center>
<a href="dash_overview">
{% include images/image.html imagePath = "../assets/images/img_blog/mainpage22/Main22_Vega_Cars_Dash.png" imageCaption =  ""%}
</a>
<br><b>
The 'cars' dataset of Vega shown in a Dashboard created with Dash.
 
</b><br>
</center>
<br>

Continue on [Fundamentals](fundamentals) ... 


## Time Series

A common use case is to predict this year's data from last years data. <br>
Once such a prediction was made, you might want to point out clearly the deviation of new value from the prediction. 

<br>
<center>
<a href="time_series_brush">
{% include images/image.html imagePath = "../assets/images/img_blog/mainpage22/Main22_Stocks_Brush.png" imageCaption =  ""%}
</a>
<br><b>
You see here the actual value and the predicted value. 
</b><br>
</center>
<br>


<br>
<center>
<a href="time_series_regression">
{% include images/image.html imagePath = "../assets/images/img_blog/mainpage22/Main22_Stocks_Regression.png" imageCaption =  ""%}
</a>
<br><b>
You see here the actual value and the predicted value. 
</b><br>
</center>
<br>

Continue on [Time Series](time_series_overview) ...


## Categorization

Some Machine Learning algorithms are shown here.<br>

<br>
<center>
<a href="cat_overview">
{% include images/image.html imagePath = "../assets/images/img_blog/mainpage22/51_PT5_Expectation.png" imageCaption =  ""%}
</a>
<br><b>
A standard example for classification.
</b><br>
</center>
<br>


The 'Iris' data is the standard data set used for clustering and classification.

<br>
<center>
<a href="cat_kmeans">
{% include images/image.html imagePath = "../assets/images/img_blog/Python/BDF/30_BDF_CAT/alt_09_C_iris_kmeans.png" imageCaption =  ""%}
</a>
<br><b>
A standard example for classification.
</b><br>
</center>
<br>

Continue on [Categorization](cat_overview) ... 

Machine Learning (i.e. no neuronal networks) concludes the part on Python. (No PyTorch here.)

---

# Julia


For Artificial Intelligence (i.e. neuronal networks), Julia might have some advantages. 
[Flux.jl](https://fluxml.ai/Flux.jl/stable/) is often considered as the AI library to go to. Before using Flux, you might want to acquire good skills on Julia first.

Migrating from Python to Julia is on one side simple but on the other side also at least time-consuming.
Simplicity stems from two similarities in particular:
- Dataframes
- Vegalite

## Dataframes in Julia

Dataframes are also available in Julia. They share similarities, but they are not equal.  

- [Julia Dataframes](julia_df) - How work on dataframes in Julia?


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

## Vegalite

The Altair library used for Python above is a wrapper of Vegalite. Vegalite is a common visualization package in Julia.


## Finally

If this all here is too long to read and seems to be too complex, remember that somebody said:

>
    "You don't need to know all solutions. Just one that works for you."
    