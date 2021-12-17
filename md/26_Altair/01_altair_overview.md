---
layout: 20_python
title: Altair Listing
permalink: /altair_overview
---

## Altair Overview


### Altair Listing

Find details on how to improve and beautify a chart in the [Altair listing](altair_listing).


### Altair Fundamental example

The [Altair listing](altair_listing) assumes that you have a fundamental chart running.

This is an example for such a fundamental chart.

>
    from vega_datasets import data
    import altair as alt
    cars = data.cars()      
    chart = alt.Chart(cars).mark_point().encode(
        alt.X(
            'Horsepower', 
        ),
        alt.Y(
            'Miles_per_Gallon',
        ),
        alt.Color(
            'Origin',
        )
    )
    chart.show()

This notation is a bit more complex than the 'bare minimum' notation, because it uses e.g. 'alt.X'. However, it is much easer to fit in the extra configurations described in the listings.

The image should be shown in a browser and should look as shown below. 

<center>
{% include images/image.html imagePath = "../assets/images/img_blog/img_altair/altair_basic.png" imageCaption =  ""%}
The combination of Vega datasets, dataframes and Altair provides an appealing chart with little and straightforward coding.
</center>

- You are welcome expand from this example with content on the external [Altair References](altair_references).
- The info needed to do the [examples on this website](altair_stories) are on the [Altair Listing](altair_listing).



### Bridges between the worlds of Python and of Julia

Dataframes are a great bridge between Python and Julia.

Vegalite is another great bridge between Python and Julia.

Vegalite.jl on Julia side, and Altair on Python side. The JSON notation for Vega works on both sides.

Vegalite is based on Vega which in turn is based on the powerful D3 (Data-Driven Documents) library. Altair is the Python equivalent to make use of Vegalite. 

You might want to have a look how elegantly data retrieval is done in Julia. 
Piping reduces the code to a minimum, while still being readable. 
- [Vega Cars in Julia](https://www.queryverse.org/VegaLite.jl/stable/gettingstarted/tutorial/#Channel-properties-1)

Unlike Altair, in Julia, the JSON notation is used.


### Several Configuration Possibilities in Altair

Only one possibility for configuration is usually presented here. It shall be pointed out though that there typically are several solutions. Particularly, as Altair offers three possibilities for configurations:

- “Global Config” 
- “Local Config” 
- “Encoding channels"

So, naturally you find other solutions or develop your own, better fitting solution.


