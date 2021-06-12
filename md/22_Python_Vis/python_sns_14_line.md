---
layout: 10_generic
title: Line Plot
permalink: /line_plot
---

# Line Plot


A possibly interesting question could be, if the fuel consumption by cars originating from the US decreased during this time span.
Cars from Japan and Europe have been assumed to be lighter and 'less thirsty'.

<br><br>
Does the data back this assumption?
<br><br>
{% include images/image.html imagePath = "../assets/images/img_blog/54_SAC_Cars_TS_Reg.png" imageCaption =  ""%}

The Split-Apply-Combine-pattern together with linear regression shows three lines, one for each region of origin. 
Obviously, the number of miles per gallon increased as a trend for all cars or a region. At a closer look, the line for the USA has a sligthly steeper slope. 


## Comments on the Line Plot

Some relationships in a dataframe are better revealed with one type of visualization than another.
Best practices and exprience helps to determine appropriate columns to choose from. It is helpful, when the language is forgiving, i.e. the program neither crashed nor refuses to come back when the choice of data turned out to be unfortunate. 

Here, we can find from the column names that the cylinders are in column 1, and we stick with the miles per galon in column 2. 

>
    xValue = colNames[2]
    yValue = colNames[1]

Then, you are ready to plot the data

>
    myPlot = sns.barplot(
        data=df,
        x=xValue, 
        y=yValue,         
        orient="v", 
        edgecolor="k",
        palette="Blues",
        saturation=0.5,
        ci=67,
    )

- The palette "Blues" contains a fine-tuned pattern of blue colors.
- There is a good recommendation on saturation (of the color of the bars), with "0.5" being a value that subjectively adds to the beauty of the plot.
- The vertical orientation is specified with 'v' for sake of completeness as it is the default.
- The confidence interval (ci) was chosen to be about 1 sigma.


## References 

- Check the [scatter plot on this site](scatter_plot) for the framework. Identical parts are not repeated here. Only differences and noteworthy are pointed out.

- Check the [Documentation on the Seaborn Line Plot](https://seaborn.pydata.org/generated/seaborn.lineplot.html) for further parameters.