---
layout: 26_altair
title: Vega Cars Theme
permalink: /vega_cars_theme
---

## Vega Cars Expanded - Theme

This is the result of the steps described below.


<center>
{% include images/image.html imagePath = "../assets/images/img_blog/Python/BDF/20_BDF_ALT/vegacarsexpanded_theme.png"%}

<br><b>
The purpose of this graph with respect to content is the show the relationship between weight and fuel consumption. 
</b><br>

</center>



## Define and Use a Theme

Let's redo the previous example on [Vega Cars Expanded](vega_cars) using a theme. The main difference is some work on the legend.

### Using a ‘Theme’

You need to register and enable the theme such that it affects your chart.

>
    from myTheme_file import myTheme

>
    alt.themes.register('myTheme', myTheme)
    alt.themes.enable('myTheme')


### Define a ‘Theme’

Using a theme can make your main coding much more concise. A theme is a collection of your choice of recurring chart configurations. You can further change the look of all your charts easily by just making the change once in your theme.

You can outsource the theme to an extra file. This extra file essentially contains a function. This function returns a ‘configuration’.

>
    def myTheme():
    ...
    return {
        'config': {
            "padding": {"left": 25, "top": 25, "right": 25, "bottom": 20},
            "mark": {
                "type": "area",
                "color": "darkgreen", #"red",
                "strokeWidth": 3.5,
                "opacity": 0.9,
                },
            "view": {
                "width": 800, 
                "height": 550,  
            ...
            "legend": {
                "cornerRadius": 5,                
                "titleFontSize":18,  
                "titleAlign":"center",           
                "rowPadding":5,           
                "titlePadding":10,           
                "padding":5, 
                "labelFontSize": 16,
                "symbolSize":8,
            },              

You can overwrite though a property set in the theme for your specific chart.

The configuration part in the 'main' program is now very lean and essentially contains the title and subtitle.

>
    myChart = myChart.properties(
        title={
            "text": myTitle, 
            "subtitle": mySubtitle,
        },  
        autosize=alt.AutoSizeParams(
            type='fit',
            contains='padding'
        ),
    )  
