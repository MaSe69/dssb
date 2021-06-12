---
layout: 10_generic
title: Box Plot
permalink: /box_plot
---

# Box Plot with Additonal Strip Plot

Compared to the bar plot with confidence interval, the boxplot gives more information about the distribution of the data around the average. Further, the data outside the confidence interval are visualized. 
Additionally, it shows a second average for a subset of the data.

The plot for the dataframe based on 'cars' indicates the distribution for fuel consumption. The boxes show the average, the disribution and outliers. Additionally, the second plot shows the average fuel consumption for the group of cars with origin from Europe.
<br><br>
<center>

{% include images/image.html imagePath = "../assets/images/img_blog/Python/44_BDF_Box.png" imageCaption =  ""%}

The European average was consistently above the total average, but the gap was closing over time. 

</center>

With increasing details on the plot, coloring get more tricky. 
As coloring should not distract from the message, here no pallete but only single colors were used. 
For highlighting the added data from the strip plot, instead of the prevailing blue, a red color was used, but still of a pale style.

>
    boxColor = "#86a7ba"
    pointcolor = "#99474a" 

## Comments on Box Plot

We continue on the fuel consumption over time. Further, there not much new with respect to dataframe, x-value and y-value, color, saturation. 

Then, you are ready to plot the data

>
g1 = sns.boxplot(data=df, 
    x=xValue, 
    y=yValue, 
    orient="v", 
    linewidth = 1.5, 
    width=.7, 
    color= boxColor, 
    saturation=0.9, 
    whis=1, 
    fliersize=5)

- The linewidth and the width can be used to optimize the beauty. 
- Using parameters whis and fliersize you configure the visualization for the outliers, depending on how much emphasis you want to give to them.

    
## Comments on the Strip Plot


It might be of interest, how a single car or group of cars performs with respect to the complete set of data.
In this case, we selected the European cars and got the average for them per year.

>
    dfEU = df.loc[df.Origin == "Europe"]
    dfEU = dfEU.groupby(xValue).mean()

The strip plot is just added to the box plot.
>
g2 = sns.stripplot(data=dfEU, x=xValue, y=yValue, size=8, color=pointcolor, linewidth=2, marker="o", jitter=0) 

There are is not much that cannot be easily guessed.
- jitter can help to make several datapoints visible that otherwise would be overlapping, but this is not needed here.


## References 

- Check the [scatter plot on this site](scatter_plot) for the framework. Identical parts are not repeated here. Only differences and noteworthy are pointed out.

- Check the [Documentation on the Box Plot](https://seaborn.pydata.org/generated/seaborn.boxplot.html) for further parameters.
- Check the [Documentation on the Strip Plot](https://seaborn.pydata.org/generated/seaborn.stripplot.html) for further parameters.