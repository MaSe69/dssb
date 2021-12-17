---
layout: 26_altair
title: Altair Chart
permalink: /altair_chart
---

# Altair Chart

###	Set chart height and width

>
    chart = chart.properties(
        height=600,   
        width=900, 
        autosize=alt.AutoSizeParams(
            type='fit',
            contains='padding'
        ),
    )  

The other parameters just worked out to make the chart to behave more beautiful.

### Set title text

Insert to the chart properties a parameter for the title and add the text to it.

>
    chart = chart.properties(
    ...
    title={
        "text": "Cars and Properties", 
    },  
    ...
    )   

Certainly, you can replace the String for the text with a variable.


### Set subtitle text

Underneath the title, you can insert a subtitle.

>
    chart = chart.properties(
    ...
    title={
        "text": myTitle, 
        "subtitle": mySubtitle,
    },  
    ...
    )   

Multiple rows for subtitles are a great feature of Altair. 

>
    myTitle =  "Cars and Properties"
    mySubtitle1 =  "Different Regions"
    mySubtitle2 =  "Different Number of Cylinders"
    mySubtitle = [mySubtitle1, mySubtitle2]


### Change the title font size

>
    myChart = myChart.configure_title(
                fontSize=26,
                subtitleFontSize=18,
            )   


### Change the shape of the points
>
    point=alt.OverlayMarkDef(
        filled=False, 
        size=80, 
        fill='white',   
        ), 

mark_line(
    opacity=0.85,
    strokeDash=[4,2],
    point=alt.OverlayMarkDef(
        filled=False, 
        size=80, 
        fill='white',   
        ), 