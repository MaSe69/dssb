---
layout: 26_altair
title: Altair Chart
permalink: /altair_types
---

# Types of charts

Each chart is of type. <br>
Some types share configurations, but some configurations are unique to some types.

The most commonly used types include:
- Scatter
- Line
- Area
- Bar

Commonly, you want to adjust:
- Sizes
- Colors
- Shapes

The pattern is to add type specific configuration parameters to the brackets directly after the type, e.g. 

> 
    myChart = alt.Chart(df).mark_point(size=20).encode(...)

As the 'chart with points' has (only) points, the size affects these points.


## Scatter

What elsewhere is called scatter plot is the chart of type points in Altair.

> 
    myChart = alt.Chart(df).mark_point().encode(...)

### Configure the points

It can worthwhile changing the size of the points or to consider filling them with different colors.

>
    myChart = alt.Chart(df).mark_point(
        size=80, 
        filled=False, 
        fill='lightgrey', 
        color='red',
    ).encode(

In this example, all points would be red, except when you use the 'alt.Color' to distinguish variables. Then, the colors of alt.Color overwrite this setting.        

## Line

Line charts are created with the 'mark_line' command.

>
    alt.Chart(source).mark_line().encode(...)

### Configure the lines

Commonly used configuration changes include the width of the lines, modifying it from solid to dashed and to change the color.

>
    size=1.2
    opacity=0.85,
    strokeDash=[4,2],
    color=red

As with the points, alt.Color would overwrite the color. Opacity is a nice feature to blend the colors together.

In a line chart, you can also have points. The points can, for instance, indicate the 'real' data whereas the lines indicate the trends.
If you want these points, you can add to the configuration for the lines an overlay definition.

>
    point=alt.OverlayMarkDef(
        size=80, 
        filled=False, 
        fill='white',   
        ), 

You can stack a line chart using the parameter 'chart' for the y-axis:

>
alt.Y(  ...
        stack=True,
        ), 


## Area

Area charts are created with the 'mark_area' command.

>
    alt.Chart(source).mark_area().encode(...)

### Configure the areas

You can stack an area chart using the parameter 'chart' for the y-axis:

>
alt.Y(  ...
        stack=True,
        ), 




## Bar

Line charts are created with the 'mark_bar' command.

>
    alt.Chart(source).mark_bar().encode(...)

### Configure the bars


## Heat

Heat charts are created with the 'mark_rect' command.

>
    alt.Chart(source).mark_rect().encode(    

### Configure the rectangles




