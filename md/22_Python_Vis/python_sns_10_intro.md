---
layout: 10_generic
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
- [Histogram Plot](hist_plot)
- [Bar Plot](bar_plot) (both horizaontally and vertically)
- [Line Plot](line_plot)

There is an abandunce of other charts, which in practice are used rather rarely.
- [Box Plot with Additonal Strip Plot](box_plot)
- heat maps
- violin charts
- [Geo Plot]()

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

It con10_genericesumably available in the USA between 1970 and 1982.

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


