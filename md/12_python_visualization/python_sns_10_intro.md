---
layout: 20_generic
title: Python Visualization
permalink: /python_visualization
---

# Visualizations

Several libraries can be used to visualize the content of a dataframe, see the [visualization library](visualization_python_references)

## The Visualization Lifecylce

Visualization Lifecycle can be roughly subdivided into 3 areas:
- Explorative Data Analysis
- Reporting
- Forecast



## Tooling

The available plots are in practice dominated by 
- [Scatter Plot](scatter_plot)
- [Bar Plot](bar_plot) (both horizaontally and vertically)
- line charts
- geo maps

There is an abandunce of other charts, which is used in practice rarely.
Though their usage can be very thoughful in special cases, seemlingly they are often used for the sake of using them, e.g. heat maps, violin charts.

## Beauty in Visualization

Certainly a beautiful dataframe should be visualized in a beautiful way.
The definition of beauty holds true here as well, i.e. beauty does not mean to use an exotic and colorful plot.

Visualization is in the service of insight.
The point to be made by a visualization should become as clear as possible. It must not be obscured or even falsified by any concept of beauty.

Aspect ratio is important. A 4:3 ratio is a good starting point, deviate only for good reason.

Surprises shall be pointed out, expected information should be softened.

Texts should be readible by persons with normal eyesight.

Colors should be limited to two to three.
There are extensive theories on fitting colors, and many designers who already applied them successfully.
At least, do not mix pale and bright colors, except for good reason.



## Example: 
### The CARS Dataframe

This dataframe "cars" can be easily found and downloaded.

It con20_genericesumably available in the USA between 1970 and 1982.

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

