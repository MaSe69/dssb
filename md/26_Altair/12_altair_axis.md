---
layout: 26_altair
title: Altair Chart
permalink: /altair_axis
---

# Altair Axis

### Modify the axis label

If you do not set the title, the name of the variable is shown as the text at the axis, e.g. 'Weight_KG'. 
If you want to change this text, you need to set the variable 'title'. 

>
    alt.X(
        'Weight_KG', 
        title="Weight [KG]", 
        ),

If you do not want to show a text at all, simply set the title to no character at all, i.e. title="" .
<br>This works the same for both x-axis and y-axis.

### Modify the axis scale


If you do not want to restrict the display to the minimum and maximum values that are typically used,
you can specify the minimum and maximum yourself.

>
    alt.X(
        'Weight_KG', 
        scale=alt.Scale(domain=[0, 717])
        ),

Certainly, you can compute the end points yourself.

>
        scale=alt.Scale(domain=(xMin, xMax)),        


Personally, I like a bit more space between the data points and the edges.

>
        xMax = df.Horsepower.max() * 1.1

### Configure the ticks

You can set the number of ticks, which you could of course compute with respect to the min and max values.

>
        axis=alt.Axis(tickCount=10),

You can also set ticks at specified values.

