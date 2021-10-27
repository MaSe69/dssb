---
layout: 20_python
title: Altair Listing
permalink: /vega_cars
---

# Altair: Cars Example

This is the result. The details are described below.

{% include images/image.html imagePath = "../assets/images/img_blog/img_altair/myCars.png" imageCaption =  ""%}


### Import Vega Data

There is a rich library of data within Vega, ready to be used in such example.
- [GitHub: Vega Datasets Listing](https://github.com/vega/vega-datasets/tree/next/data)

 The "cars.json" file found there is often used.
 It can be downloaded and converted to a Pandas dataframe.

>
    from vega_datasets import data
    df = data.cars()


### Create a scatter plot

A scatter plot in Altair is 'mark_point'. The (...) here mean that details are omitted.

>
    import altair as alt
    myChart = alt.Chart(df).mark_point().encode(...)


