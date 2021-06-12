---
layout: 10_generic
title: Box Plot
permalink: /hist_plot
---

# Histogram

A histogram is a great way to explore an unknown data set and hence a standard tool in explorative data analysis (EDA). <br>
Particularly, changing the so-called bin sizes can lead to a good first impression on the information hidden in the data.
<br>
From the dataframe based on 'cars', we would like to know the distribution of horsepower of all cars.

<center>
<br>
{% include images/image.html imagePath = "../assets/images/img_blog/Python/45_BDF_HistPlot.png" imageCaption =  ""%}

There are two peaks, a big one at the lower end and a smaller one at the higher end.
</center>

## Comments on Hist Plot

For vertical columns, only use the x-value. 
For horizontal columns, only use the y-value. 

Certainly, binwidth and binrange can be determined programatically depending on the data, but here they are just used to play around.

>
    myPlot = sns.histplot(data=df, x=xValue, binwidth=10, binrange=[0, 250], palette="Reds", hue=zValue, element="step")


- Adding the hue-parameter to visualize an additional dimension seemed to be appropriate here, because there is such a clear dependence between horsepower and cylinders.
- Adding the step-element 'merged' the columns belonging to the same number of cylinders, making the plot easier to read.


## References 

- Check the [scatter plot on this site](scatter_plot) for the framework. Identical parts are not repeated here. Only differences and noteworthy are pointed out.

- Check the [Documentation on the histplot](https://seaborn.pydata.org/generated/seaborn.histplot.html) for further parameters.