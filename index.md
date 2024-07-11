---
layout: 01_landing
title: Beautiful Dataframes
permalink: /index
---


This is a web site on some Data Science topics.<br>
My focus in 2024 shifted back to time series. 

It includes still some content that I taught during an academic course on 'Data science in Python' leading to a bachelor degree.<br>


## Modelling - Time series

I had started using the library Altair. Currently, I am using Plotly only. 

- [Time Series](time_series_overview) - How to work with time-dependent data?.


# Setup and Coding

Okay, let's get started with the [Setup 2024 for Pandas and Plotly on Ubuntu](setup_ubuntu_pandas_plotly)

Mostly, I use Python, Pandas and Plotly here.
- [Python - Some Python for use with Pandas](python_refresher) - Lists, dictionaries, comprehensions, ...
- [Pandas - Overview](pandas_overview) - Create, work on columns, ... 
- [Plotly - Configurations](plotly_configurations) - Configure graphs, ... 

Special topic of interest:
- [Pandas - Rows](pandas_rows24) - How to delete the last row of a Pandas dataframe?
Special topic of interest:
- [Pandas running in a Docker container](pandas_docker) - How run a Python program using Pandas in a Docker container?


# Some results 

## First Names

Let's start with a data set that is straightforward to consume and to visualize.

The statistics department in Scotland has a great website from which a lot of interesting data can be downloaded, e.g. [Birth names](https://www.nrscotland.gov.uk/statistics-and-data/statistics/statistics-by-theme/vital-events/names/babies-first-names/babies-first-names-2022)
<br>
How does my first name compare to the currently most popular male first name?


<center>
{% include images/image.html imagePath = "../assets/images/img_blog/Python_2024/FirstNames/C_25_Line_Fixed_Names.png" imageCaption =  ""%}
Total number of names per year in Scotland shown for tow specific first names.
</center>

Well, my first name has some potential for growth. However, considering the increasing diversity of names and hence the lower maximum values for the top names, the difference to the top names is getting smaller. 

More on the technical part of this analysis and more on first names can be found here: [Pandas - Analysis  first names](Pandas_Analysis_First_Names)


---

# Julia

There is no update on the Julia content since about 2021.
If you need the content on Julia, please copy it. I will remove at least the links from the landing page soon. 

- [Julia Dataframes - Columns](julia_columns) - How to work on columns of a Julia dataframe?
- [Julia Dataframes - Rows](julia_rows) - How to work on rows of a Julia dataframes?
- [Julia Dataframes - Transpose](julia_transpose) - How to transpose a Julia dataframe?
- [Julia Dataframes - Operations](julia_df_ops) - How to operate on a Julia dataframes?
- [Julia Dataframes - Dataframe](julia_df) - How to work on the complete Julia dataframe?
- [Julia Dataframes - Visualization](julia_visualization) - How to visualize a Julia dataframe?
    