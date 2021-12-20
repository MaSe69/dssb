---
layout: 26_altair
title: Vega Cars
permalink: /vega_cars_interactive
---

# Vega Cars Interactive

This chart provides more information than its static predecessor, because you can zoom into each cloud of points and get the details, particularly the name of the car type.

{% include altairhtml/vegacarsexpanded_interactive.html %}


The tooltip is defined within the chart configuration.

>
    myChart = alt.Chart(df).mark_point(
        size=60, 
        filled=False, 
    ).encode(
        alt.X(
            'Weight_KG', 
            title="Weight [KG]", 
            scale=alt.Scale(domain=(xMin, xMax)),        
            axis=alt.Axis(tickCount=10),
        ),
        alt.Y(
            'Consumption_lper100km', 
            title="Consumption [Liters per 100 km]",
            scale=alt.Scale(domain=(yMin, yMax)),        
            axis=alt.Axis(tickCount=6),
        ),
        alt.Color(
            'Origin',
            title="Origin",
            scale={"range": [
                    "blue", "green",  "#e45756"
                ]}   
        ),
        alt.Shape('Cylinders', 
            scale=alt.Scale(range=['triangle-left','square', 'triangle-right','circle', 'cross'])
        ),    
        tooltip=['Name', 'Year', 'Weight_KG', 'Consumption_lper100km', 'Cylinders'],            
    )

