---
layout: 26_altair
title: Vega Cars
permalink: /vega_cars_multi_selection
---

# Vega Cars Multi Selection

In this chart, you can select one or multiple 'Origins'. 

The interactivity, i.e. zooming and tooltip, is also available. The theme defined in previous examples is re-used with minor modifications.<br>
A feature of this approach is to use an additional chart as both the 'legend' and as 'the tool for selection'.

<center>
<br>
{% include altairhtml/vegacars_i_multiselect.html %}
<br><br>
Multiple selection applied to the Vega Cars dataset.
<br>
</center>
<br><br>


## Solution approach

In a previous example, [single selection](vega_cars_interactive) using a drop down list was shown. Unfortunately, Altair or Vegalite tooling dos not permit to expand that solution to multiple select in a straightforward way. 

In real life, multiple select is an important use case. Hence, it is worthwhile exploring an alternative solution approach. The approach presented here is based on the technique used for linking several charts and useful for more advanced linking of chart content.

### Combining charts

You can combine charts either vertically using vconcat or horizontally using hconcat.

>
    myChart = alt.vconcat(myPoints1, mySelRect1, center=True)

Comments:
- The sequence specified defines which chart is the upper one.
- The "center" parameter moves the selection chart from the left side to the center. 


### Main Chart = Scatter Plot = Chart of type points

The main chart which displays the data is enriched by a 'transform_filter' with a specified 'selection'. 

>
    myPoints1 = alt.Chart(df).mark_point(
        ...
    ).encode(
    ).transform_filter(
        selection
    ).interactive() 


You need to have specified the multiple selection for a column of your choice.

>
    colName = "Origin"
    selection = alt.selection_multi(fields=[colName])


A chart of type 'rectangle' is used for the 'selection options'

>
    mySelRect1 = alt.Chart(dfSel).mark_rect(
    ).encode(
        alt.X(
            colName,
            title=colName,
            axis=alt.Axis(labelAngle=0),
        ), 
        color= alt.condition(
            selection, 
            alt.Color('Origin:N',
            ) , 
            alt.value('grey')),
        ).add_selection(selection)

Mind that the selection appears twice: 
- in the condition for the color
- in the 'add_selection' for the chart itself.

## Comments

- The colors only need to be defined in the main chart, the selection chart re-uses those colors.


## References

Thanks is particularly due to:

- [Altair Intro by Jim Vallandingham](https://vallandingham.me/altair_intro.html)
- [Solution Approach by TristanK27](https://github.com/altair-viz/altair/issues/1115)