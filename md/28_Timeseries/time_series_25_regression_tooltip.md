---
layout: 20_python
title: Time Series Regression
permalink: /time_series_tooltip
---

# Tooltip for a Time Series with Linear Regression

The task here is to **apply interactivity in a value-adding way to a data with a regression**. 

<center>
<br>
{% include altairhtml/20_BDF_ALT/TimeseriesTooltip.html %}
<br><br><b>
A 'slider' that can be moved on the x-axis triggers the respective values to be displayed.
</b><br>
</center>
<br><br>

Interactivity might be regarded unnecessary. However, the few seconds that a user spends more on your message when trying out this interactivity might make the difference, if he or she buys in on your message.


## Solution idea and some details 

This solutions copies much of the Altair documentation example, see [Altair - Multi-Line Tooltip](https://altair-viz.github.io/gallery/multiline_tooltip.html). <br>
This solution continues a previous example using [Linear Regression](time_series_regression)

Some adaptations might be worth mentioning. 

First, the original chart already consists out of 4 layers. Adding this multi-line interactivity adds another 5 layers. 

>
    chart = chart + selectors + rules + regrText + modelText + testText

The layers for 'nearest' and selectors and rules were copied unchanged, with minor or obvious modifications.

A noteworthy feature is the positioning of the text using an existing layer. 
For instance, the values of the prediction are positioned by using the layer for the regression.

>
regrText = myRegression.mark_text(
    align="left",
    dx=10,
    dy=15,
    fontSize=16,
    fontWeight=200,
    color='green',
).encode(text=alt.condition(nearest, "Profit_y:Q", alt.value(" ")))


This implies that the text to be displayed must be available in the dataframe that is used with the original layers. 

