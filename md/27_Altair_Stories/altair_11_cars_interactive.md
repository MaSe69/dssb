---
layout: 26_altair
title: Vega Cars
permalink: /vega_cars_interactive
---

# Vega Cars Interactive

This chart provides more information than its static predecessor, because you can zoom into each cloud of points and get the details, particularly the name of the car type.

{% include VegaCarsScatterTooltip.html %}


The tooltip is defined within the chart configuration.

>
    myChart = alt.Chart(df).mark_point().encode(
        alt.X(
            'Weight_KG', 
            title="Weight [KG]", 
            scale=alt.Scale(domain=[2400, 600])
            ),
        alt.Y('Consumption_lper100km', 
            ...
        tooltip=['Name', 'Year', 'Weight_KG', 'Consumption_lper100km', 'Cylinders'],
    ).interactive()


Obviously, this chart is subdivided into three charts using the origin as a split criteria.
Similar syntax splits the chart in rows.

>
        column=alt.Column(
            'Origin:N',
            title="",
        ),  


Mind that interactivity is not available in PNG-files. Here, HTML-files are used.
Hence, the full coding might look like this:

>
    fileExtensions = ".html"
    fullname = path + basename + fileExtensions


