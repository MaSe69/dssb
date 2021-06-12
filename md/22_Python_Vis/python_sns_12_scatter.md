---
layout: 20_python
title: Scatter Plot
permalink: /scatter_plot
---

# Scatter Plot

We use the following approach here:
- use the Seaborn call for the main graph
- use the Seaborn parameters as much as possible
- use the Matplot parameters to accomplish the remaning task

Check the [Documentation on the Seaborn Scatter Plot](https://seaborn.pydata.org/generated/seaborn.scatterplot.html) for further parameters.


Two numerical columns of the dataframe based on the data 'cars':
<br><br>
<center>

{% include images/image.html imagePath = "../assets/images/img_blog/Python/41_BDF_Scatter.png" imageCaption =  ""%}

A heavier car runs less miles for a gallon - good that data also shows this.

</center>

## Scatter Plot in Seaborn

These are all imports needed
>
    import pandas as pd
    import matplotlib.pyplot as plt
    import seaborn as sns


Once you have got your dataframe, you can specify two dimensions to see the relationship between these values.

You might want to get a list of all column names

>
    df = pd.read_csv(filename, nrows = 1)
    colNames = df.columns.values

to specify your x-value and y-value

>
    xValue = colNames[5]
    yValue = colNames[1]

Then, you are ready to plot the data

>
    myPlot = sns.scatterplot(data=df, x=xValue, y=yValue)
    
## Beautifications

### Colors

Technically, there are 3 colors to be specified. 

- A color for the background of the plot, the so-called face color.
- A color for the background of the figure, i.e. the edge around the plot, let's call it edge color.
- A color for 'all the rest', i.e. the data points, the ticks, all text, etc.

It is sufficient to have two colors, e.g. 

>
    textColor = "#e5f6ff"
    edgeColor = "#061727"
    faceColor = textColor

Further, you can specify the shape of the data, e.g. squares, and their sizes (s).

>
    myPlot = sns.scatterplot(data=df, x=xValue, y=yValue, color=edgeColor, marker="s", s=40)


The edge color is defined for the figure:

>
    fig.set_faceColor(edgeColor)    

The color for the ticks is set with Matplotlib parameters
>
    ax.tick_params(axis='x', colors=textColor, rotation=0)
    ax.tick_params(axis='y', colors=textColor)    

### Texts

When working with many graphs, it is time-saving to have the texts at one place, e.g. 

>
    superTitle = "Scatter Plot"
    title = "Plotting " + yValue + " vs. " +  xValue
    xLabel = xValue
    yLabel = yValue

This is also the place to change the lable of the axis, which is then made effective with the Matplotlib parameters:

>
    ax.set_xlabel(xlabel = xLabel, fontsize=14, color=textColor, labelpad = 8)
    ax.set_ylabel(ylabel = yLabel, fontsize=14, color=textColor, labelpad = 8)    


### Proportions 

Optimizing proportions is rather an art, which might depend on the number of data points, the amount of text and the overall style. Technically, it is adjusted using the labelpads and the general settings for figure and its subplot(s):

>
    fig, ax = plt.subplots(figsize=(8, 5))
    plt.subplots_adjust(left=0.12, right=0.91, top=0.80, bottom=0.15)



## Saving

Mind that saving the plot can have some caveats, but once you have got the full path to save your plot to, this coding should do

>
    fig.savefig(
        fullPathPlot,
        dpi=fig.dpi,
        facecolor=fig.get_facecolor(),
    )