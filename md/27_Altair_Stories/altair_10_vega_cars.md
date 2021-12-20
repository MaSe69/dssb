---
layout: 26_altair
title: Vega Cars
permalink: /vega_cars
---

# Vega Cars - Expanded

This is the result of the steps described below.


<center>
{% include images/image.html imagePath = "../assets/images/img_blog/img_altair/vegacarsexpanded.png" imageCaption =  ""%}

<br><b>
The purpose of this graph with respect to content is the show the relationship between weight and fuel consumption. 
</b><br>

</center>


The full program consists of the following steps:

- Import the data to a dataframe
- Work on that dataframe
- Select 4 columns of the dataframe to be shown in the chart.
- Modify the chart

More work is definitely needed to get to a beautiful chart. This is meant as a starter to show how to get going. 

Themes make such configurations much easier to digest. Hence, here - without themes - only a few configurations are shown. You might need come back to it when you want to overwrite configurations made in a theme.


## Import Vega Data

There is a rich library of data within Vega, ready to be used in such example.
- [GitHub: Vega Datasets Listing](https://github.com/vega/vega-datasets/tree/next/data)

 The "cars.json" file found there is often used.
 It can be downloaded and converted to a Pandas dataframe.

>
    from vega_datasets import data
    df = data.cars()


## Work on the dataframe

You might want to add additional columns on the dataframe. One advantage is to save the dataframe as csv-file.
Alternatively, you could do such transformations in Altair.

>
    df["Weight_KG"] = df.Weight_in_lbs / 2.20462
    df["Consumption_lper100km"] = 235 / df.Miles_per_Gallon

The figures used here are just taken from the internet.

Another transformation is rounding and type conversions.

>
    df.Consumption_lper100km = df.Consumption_lper100km.astype(float).round(2)
    df.Cylinders = df.Cylinders.astype(str)

You might want to have a look at [Pandas listing](listing_pandas_operate) for more details.

### Create the scatter plot

A scatter plot in Altair is 'mark_point'. 

>
    myChart = alt.Chart(df).mark_point(
        size=60, 
        filled=False, 
    ).encode(
        alt.X(
            'Weight_KG', 
            title="Weight [KG]", 
            scale=alt.Scale(domain=(xMin, xMax)),        
            axis=alt.Axis(tickCount=10),
        ),
        alt.Y(
            'Consumption_lper100km', 
            title="Consumption [Liters per 100 km]",
            scale=alt.Scale(domain=(yMin, yMax)),        
            axis=alt.Axis(tickCount=6),
        ),
        alt.Color(
            'Origin',
            title="Origin",
            scale={"range": [
                    "blue", "green",  "red"
                ]}   
        ),
        alt.Shape('Cylinders', 
            scale=alt.Scale(range=['triangle-left','square', 'triangle-right','circle', 'cross'])
        ),    
    )


The min and max values for the axis are computed from the respective columns of the dataframe.

>
    xMin = df.Weight_KG.min()
    xMax = df.Weight_KG.max()
    yMin = 0
    yMax = df.Consumption_lper100km.max()*1.1

Altair uses sensible choices as default, but there is always some potential for optimization.


### Configure the plot

Define the title and the subtitle. The subtitle can have many lines, which is can be a very useful feature, though not really needed in this example.

>
    myTitle =  "Vega Cars - Expanded"
    mySubtitle1 =  "Relationship between weight and fuel consumption"
    mySubtitle2 =  "European Units"
    mySubtitle = [mySubtitle1, mySubtitle2]

General configurations, e.g. the background color is set to one of the main colors of this website. 

>
    myChart = myChart.properties(
        background="#c9deff", 
        padding={"left": 25, "top": 25, "right": 25, "bottom": 25},
        view={"fill": "white"},
        height=550,   
        width=800, 
        title={
            "text": myTitle, 
            "subtitle": mySubtitle,
        },  
        autosize=alt.AutoSizeParams(
            type='fit',
            contains='padding'
        ),
    )  

Without setting the font sizes, the titles would be very small.

>
    myChart = myChart.configure_title(
                fontSize=28,
                subtitleFontSize=20,
            )   

Without setting the title font sizes, the description of the axis (also called 'titles') would be very small.

>
    myChart = myChart.configure_axis(
            labelFontSize=12,
            titleFontSize=18
            )   

Changing one configuration often leads to the need to change another configuration. A dark the background color, makes the symbols of the 'Shape'-dimension hardly visible. Hence, the background color of the legend is changed here - together with some additional configurations to make the legend look nices.

>
    myChart = myChart.configure_legend(
            padding=10,
            titleFontSize=14,
            titleColor="#061f80",
            fillColor="#edf4ff",
            labelColor="black",
            symbolStrokeColor="black",
            )   

That shall be it for this example. More configurations are best placed in a theme.
