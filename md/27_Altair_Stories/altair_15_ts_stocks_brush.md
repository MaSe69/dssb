---
layout: 26_altair
title: Time Series Brush
permalink: /time_series_brush
---

# Extra Zoom Window + Multi Selection

In this chart, you can zoom on the date in the lower chart. <br>
Further, you can select a stock from the legend.
You can select multiple stocks using 'Shift'.


<center>
<br>
{% include altairhtml/20_BDF_ALT/30_20_TS_IA_Legend_Brush.html %}
<br><br><b>
Left-click on the lower chart and drag the mouse pointer for zooming in on a time window. <br> For multiple selections on the legend, press SHFT and left click.
</b><br>
</center>
<br><br>


## Relevant coding


>
   selection = alt.selection_multi
   (fields=["Abbr"], bind="legend")

>   
   myChart = (
        alt.Chart(df)
        .mark_line(
            size=3,
        )
        .encode(
            alt.X(
                "Date:T",
                title="Year",
            ),
            alt.Y(
                "Price",
                title="Stock Price",
            ),
            alt.Color(
                "Abbr", title="Stock", scale={"range": [myColor1, myColor2, myColor3]}
            ),
            opacity=alt.condition(selection, alt.value(1), alt.value(0.06)),
        )
        .add_selection(selection)
    )

>    
    brush = alt.selection(type="interval", encodings=["x"])

>    
    upper = myChart.encode(
        alt.X("Date:T", title="", scale=alt.Scale(domain=brush)),
    ).properties(height=4.5 * myHeight)

>
    lower = myChart.properties(height=myHeight).add_selection(brush)
>    
    myChart = upper & lower

## Comments

When using the chart:
- Multi selection is lost too easily.
- The zoom window can be moved but not be re-sized, it's faster to create a new one.



## References

Thanks is particularly due to:

- [Altair Intro by Jim Vallandingham](https://vallandingham.me/altair_intro.html)
- [Solution Approach by TristanK27](https://github.com/altair-viz/altair/issues/1115)
