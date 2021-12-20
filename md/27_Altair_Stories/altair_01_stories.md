---
layout: 26_altair
title: Altair Stories
permalink: /altair_stories
---


# Altair Stories

Starting from the fundamental 'Vega cars' example, Altair configurations are added.

## List of Examples

- Most common configurations are applied in [Story - Vega Cars - Expanded](vega_cars)
- First interactive elements are applied in [Story - Vega Cars - Interactive](vega_cars_interactive)
- Adoptions for time series are made in [Story - Time series](timeseries)


### Vega Car"

A point here is to make the transformations, e.g. lbs to kg, in the dataframe. It could be done in Altair using the transform operation. 


### Vega Cars Interactive


The data is split by region and the car name can be retrieved from the tooltip:

<center>
{% include images/image.html imagePath = "../assets/images/img_blog/img_altair/VegaCarsScatterTooltip.png" imageCaption =  ""%}
</center>


### Time series

Another big advantage of Altair are templates. When managing a zoo of charts, extracting the common parts into one file is a great time saver.

Mind that the template is written in the JSON notation of Vega. Overwriting settings of the template within the program is the done in the Python-style syntax.

As well known, Pandas comes with great support for time series. Altair adds great support for the x-axis. In particular, the tick labels are set in a meaningful manner. Adding, for instance, the year at the position of January on a multi-year x-axis is a little, but great feature.


### Time series area




### External sources

[Altair References](altair_references)

