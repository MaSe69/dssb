---
layout: 20_python
title: Altair Listing
permalink: /altair_overview
---

## Altair Overview

You might want to start with the fundamental example below and expand it a bit to your needs, see [Altair listing](altair_listing).<br>
When you create a lot of charts, you might want to use [Themes in Altair](altair_themes).<br>
Finally, you might benefit from some examples on putting the pieces together, see [Altair Starter Story](altair_starter_story).


### Altair Fundamental example

The [Altair listing](altair_listing) assumes that you have a fundamental chart running.

This is an example for such a fundamental chart.

>
    from vega_datasets import data
    import altair as alt
    df = data.cars()      
    chart = alt.Chart(df).mark_point().encode(
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


There is a rich library of data within Vega, ready to be used in such example.
- [GitHub: Vega Datasets Listing](https://github.com/vega/vega-datasets/tree/next/data)

 The "cars.json" file found there is often used.
 It can be downloaded and converted to a Pandas dataframe.

This notation is tailored such that the solutions of the listings fit in easier. df as usually denotes a dataframe. Mind that you always pass the correct dataframe to chart of Altair.

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


