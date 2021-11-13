---
layout: 20_python
title: Altair Listing
permalink: /altair_about
---

# Altair About

The [altair listing](altair_listing) is a page generated automatically from a dataframe.
Hence, I put the 'free text' here.

## Altair and Vegalite.jl

Dataframes are a great bridge between Python and Julia.

Vegalite is another great bridge between Python and Julia. Vegalite.jl on Julia side, and Altair on Python side. The JSON notation for Vega works on both sides.

You might want to have a look how elegantly data retrieval is done in Julia. 
Piping reduces the code to a minimum, while still being readable. 
- [Vega Cars in Julia](https://www.queryverse.org/VegaLite.jl/stable/gettingstarted/tutorial/#Channel-properties-1)

Unlike Altair, in Julia, the JSON notation is used.


## My Examples 

Currently, I provide the following examples:
- [Vega Cars](vega_cars)
- [Vega Cars Interactive](vega_cars_interactive)
- [Time series](timeseries)
- [Time series area](timeseriesarea)

The Altair gallery provides plenty of examples. Why providing some more?

The point of that gallery is to demonstrate the tooling.<br>
The point here within beautiful dataframes is to show how the tooling is used to display the content of a dataframe.


Here are some remarks on the examples.

### "Vega Cars"

"Vega cars" is a modification of the standard 'textbook' example.
It is based on a data set provided by Vega. 

I had used this data set previously for visualization using Seaborn and Matplotlib. Comparing effort and results, there was no doubt to continue with Altair.

A point here is to make the transformations, e.g. lbs to kg, in the dataframe. It could be done in Altair using the transform operation. 


### Time series

Another big advantage of Altair are templates. When managing a zoo of charts, extracting the common parts into one file is a great time saver.

Mind that the template is written in the JSON notation of Vega. Overwriting settings of the template within the program is the done in the Python-style syntax.

As well known, Pandas comes with great support for time series. Altair adds great support for the x-axis. In particular, the tick labels are set in a meaningful manner. Adding, for instance, the year at the position of January on a multi-year x-axis is a little, but great feature.


### Time series area




### External sources

[Altair References](altair_references)

