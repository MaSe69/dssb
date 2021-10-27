---
layout: 20_python
title: Altair Listing
permalink: /altair_listing
---

## Altair Listing

|  Object |  How to | Coding Hint | Link to Example | 
| :---            |    :--------   |  :--- |  :--- |  
| Get Demo Data | get demo data from Vega| from vega_datasets import data |[Vega Cars](vega_cars)| 
| Getting Started | create a first plot| chart = alt.Chart(df).mark_point().encode(...) |[Vega Cars](vega_cars)| 
| Manage Plot | save the plot on the file system| from altair_saver import save |[Vega Cars](vega_cars)| 
| Axis | label an axis| title="...",  scale=alt.Scale(domain=[...]) |[Vega Cars](vega_cars)| 
| Lines | choose colors or shape|  alt.Color(...), alt.Shape(...)]) |[Vega Cars](vega_cars)| 
| Layout | define a theme| def mytheme(): ...return ...  |[Time series](timeseries)| 
| Layout | use your theme| alt.themes.register(...)  |[Time series](timeseries)| 
| Layout | set width and heigth| myChart.properties(width=(...)  |[Time series](timeseries)| 
| Data | put csv data to Altair format| df.reset_index().melt(id_vars=...) |[Time series](timeseries)| 
| Title | add title and subtitle| title={"text":[title],"subtitle": ... |[Time series](timeseries)| 
| Axis | format for month| alt.X('yearmonth(Month):T', ...) |[Time series](timeseries)| 
| Axis | set scale and tick count| axis=alt.Axis(tickCount=10),scale=alt.Scale(domain=(...) |[Time series](timeseries)| 
| Axis | set custom colors| scale={"range": (...)]) |[Time series](timeseries)| 
| Lines | format the line and points| strokeDash=[4,2], point=alt.OverlayMarkDef(...) |[Time series](timeseries)| 
