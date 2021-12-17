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


## Scatter

What elsewhere is called scatter plot is the chart of type points in Altair.

> 
    myChart = alt.Chart(df).mark_point().encode(...)


## Line

>
    alt.Chart(source).mark_line().encode(...)


## Area

    alt.Chart(source).mark_area().encode(...)

## Bar

>
    alt.Chart(source).mark_bar().encode(...)

## Heat

>
    alt.Chart(source).mark_rect().encode(    

