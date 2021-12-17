---
layout: 20_python
title: Vega Cars
permalink: /vega_cars
---

# Altair: Modified Cars Example

Find here the result. The details are described below.
<center>
{% include images/image.html imagePath = "../assets/images/img_blog/img_altair/myCars.png" imageCaption =  ""%}
</center>
You can find the 'standard cars example' in many places. I modified it here to make the point that there is a good correlation between the weight of a car and its fuel consumption. As a European, I am more familiar with the units kilogram and liters per 100 km. 


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

### Save the chart

You can show the chart directly in a browser.
>
    chart.show()

Typically, however, I want to save the chart as a PNG file.

>
    from altair_saver import save
    fullpath = /home/..../chartName.png
    save(chart, fullpath)


For saving as PNG, there is an issue that can be fixed with an additional installation.
The interactive features are not available when using PNG.


### Formatting x-axis

On the dataframe, I earlier created a column 'Weight_KG' that I use as x-axis.
The label should indicate that the weight is not the original lbs. 
I chose to fix the scale and also to revert it, i.e. running from high value to low value.

>
    alt.X(
        'Weight_KG', 
        title="Weight [KG]", 
        scale=alt.Scale(domain=[2500, 500])
        ),

The y axis behaves similarly.

### Formatting Different (Hue) Colors, Shapes

The 'origin' is a standard column in the data set. For the purpose of demo, I give it another color scheme.

>
    alt.Color('Origin',
            scale=alt.Scale(scheme='tableau10'),   
        ),

I tried to mark the various cylinder numbers differently

>
    alt.Shape('Cylinders', 
        scale=alt.Scale(range=['triangle-left','square', 'triangle-left','circle', 'cross'])
    ),
