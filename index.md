---
layout: 01_landing
title: Beautiful Dataframes
permalink: /index
---


This is a web site on some Data Science topics.<br>
It includes content that I taught during an academic course on 'Data science in Python' in 2022 and 2023 leading to a bachelor degree.<br>

Update (January 2024):<br>
At this start of 2024, I am preparing for the repetition of this course.<ok>

# Setup and Coding

Okay, let's get started with the [Setup 2024 for Pandas and Plotly on Ubuntu](setup_ubuntu_pandas_plotly)

Mostly, I use Python, Pandas and Plotly here.
- [Python - Some Python for use with Pandas](python_refresher) - Lists, dictionaries, comprehensions, ...
- [Pandas - Overview](pandas_overview) - Create, work on columns, ... 
- [Plotly - Configurations](plotly_configurations) - Configure graphs, ... 

Special topic of interest:
- [Pandas - Rows](pandas_rows24) - How to delete the last row of a Pandas dataframe?

# Results 
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



## Modelling - Time series

- [Time Series](time_series_overview) - How to work with time-dependent data?.


## Modelling - Categorizations

- [Categorization](cat_story) - How to cluster and categorize?

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
    