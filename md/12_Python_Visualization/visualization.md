---
layout: 20_generic
title: Python Visualization
permalink: /python_visualization
---

# Visualizations

Several libraries can be used to visualize the content of a dataframe, see the [visualization library](visualization_libraries)


## Example: 
### The CARS Dataframe

This dataframe "cars" can be easily found and downloaded.

It contains information about features of cars presumably available in the USA between 1970 and 1982.

It has features that make it to a somehow beautiful dataframe, though there are also shortcomings.

{% include images/image.html imagePath = "../assets/images/img_blog/cars_dataframe.PNG" imageCaption =  ""%}

This dataframe has
- clear focus on a small set of cars
- clearly named columns (in one word, starting with capital letters)
- a unique key
- appropriately formatted figures
- a standard date format
- a categorical attribute (=Origin)

A shortcoming of this dataframe is to not contain info on the percentage of cars sold during this period. Without info outside of it, the coverage could be near to complete or too small to draw any conclusions. It also does not indicate the selection criteria for a car to be included.


### A visualization of this dataframe

A possibly interesting question could be, if the fuel consumption by cars originating from the US decreased during this time span.
Cars from Japan and Europe have been assumed to be lighter and 'less thirsty'.
<br><br>
Does the data back this assumption?
<br><br>
{% include images/image.html imagePath = "../assets/images/img_blog/54_SAC_Cars_TS_Reg.png" imageCaption =  ""%}

The Split-Apply-Combine-pattern together with linear regression shows three lines, one for each region of origin. 
Obviously, the number of miles per gallon increased as a trend for all cars or a region. At a closer look, the line for the USA has a sligthly steeper slope. 

