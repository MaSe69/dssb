---
layout: 26_altair
title: Vega Cars
permalink: /vega_cars_interactive
---

# Vega Cars - Interactive - Tooltip + DropDown Filter

## Result

This chart provides more information than its static predecessor, because you can zoom into each cloud of points and get the details, particularly the name of the car type.

Further, you can select the number of cylinders using the dropdown box below the chart.

<center>
<br>
{% include altairhtml/20_BDF_ALT/vegacars_i_dropdown.html %}
<br><br><b>
Interactive Elements: Dropdown and Tooltip
</b><br>
</center>
<br><br>


This solution does enable the selection of exactly on item of the dropdown list. Further, once you selected an item, there is no (built-in) possibility to reset to all data. Here, you can reload the page to get back to all data, but that's not an acceptable solution. Finally, the dropdown box is not very beautiful. In the next step, these issues are addressed.

For many use cases, this solution might be sufficient. Here are selected details.


## Solution Approach

The tooltip is defined within the chart configuration.


You need to define the selection items on the drop down list, i.e. selValues here. Then, you put them into an Altair selection.
>
    input_dropdown = alt.binding_select(options=selValues, name="Number of Cylinders")
    selection = alt.selection_single(fields=["Cylinders"], bind=input_dropdown)


This selection is added to the chart.

The tooltip implementation has become very simple. It is just one line and essentially contains the column names of the dataframe displayed by the Altair chart.

>
    myChart = (
        alt.Chart(df)
        .mark_point(
            size=60,
            filled=False,
        )
        .encode(
            alt.X(
                "Weight_KG",
            ...
            ),
            tooltip=["Name", "Year", "Weight_KG", "Consumption_lper100km", "Cylinders"],
        )
        .add_selection(selection)
        .transform_filter(selection)
    )


## Comments

-  Unfortunately, the tooltip might look better in some contexts than in others. "There are no options within Altair to change tooltip styles.", see [Answer by Jake VanderPlas](https://github.com/altair-viz/altair/issues/1970). 
- In 2018, the possibility to code a tooltip as above might not have been available, as can be inferred from [Jim Vallandingham's Blog](https://vallandingham.me/altair_intro.html)

