---
layout: 01_landing
title: Beautiful Dataframes
permalink: /index
---


This is a web site on some Data Science topics.<br>
It includes content that I taught during an academic course on 'Data science in Python' in 2022 and 2023 leading to a bachelor degree.<br>

Update (January 2024):<br>
Preparing for the repetition of this course, I am working on new versions of some content. 
For regular users of this page, I try not to delete content. Though, if there is a better version, it will replace the existing one.<br>

In 2023, I replaced in my programs the library Altair with Plotly. Hence, the current update will move pages using Altair to the back.


# Some Data Science in Python

Most of the work might be due to mastering Pandas and fine tuning the visualizations.
For providing you an overview, I moved the details to the layer below this page.

I currently recommend to split a task into steps:
- [Wrangling](pandas_wrangling) - How to use Pandas for data wrangling?
- [Visualization](plotly_overview) - How to visualize the content of a Pandas dataframe?
- [Modelling](pandas_modelling) - How to fit a model to the data?

My favorite modelling topics:
- [Time Series](time_series_overview) - How to work with time-dependent data?.
- [Categorization](cat_story) - How to cluster and categorize?

If you are new to the topic, you might want to start here:
- ['Python for Data Science' - Refresher](python_refresher) - What to refresh from a potentially vast Python skill set?
- ['Pandas - How do I ... work with one dataframe](pandas_how_do_I) - How to perform fundamental changes to a dataframe?
- ['Pandas - How do I ... work with more than one dataframe](pandas_two_df) - How do I split and merge dataframes?


### Altair

The library Altair offers nice features. Some of them are illustrated below.

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

### Plotly

An alternative visualization using Plotly. Plotly also offers the possibility to extend graphs to a dashboard. <br>

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

In 2022 and 2023, Python was sufficient for all my requirements. 
No updates hence on my pages on Julia dataframes. The content on Julia reflects my version and my knowledge of Julia as of 2021. 

Here are the pages on Julia dataframes you were interested in 2023.

- [Julia Dataframes - Columns](julia_columns) - How to work on columns of a Julia dataframe?
- [Julia Dataframes - Rows](julia_rows) - How to work on rows of a Julia dataframes?
- [Julia Dataframes - Transpose](julia_transpose) - How to transpose a Julia dataframe?
- [Julia Dataframes - Operations](julia_df_ops) - How to operate on a Julia dataframes?
- [Julia Dataframes - Dataframe](julia_df) - How to work on the complete Julia dataframe?
- [Julia Dataframes - Visualization](julia_visualization) - How to visualize a Julia dataframe?
    