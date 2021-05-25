---
layout: 30_topic
title: Bar Plot
permalink: /bar_plot
---

# Bar Plot

- Check the [scatter plot](scatter_plot) for the framework. Identitcal parts are not repeated here. Differences only are pointed out.

- Check the [Documentation on the Seaborn Bar Plot](https://seaborn.pydata.org/generated/seaborn.barplot.html) for further parameters.


For the horizonal bar chart, we chose the number of cylinders for the data 'cars':
<br><br>
<center>

{% include images/image.html imagePath = "../assets/images/img_blog/Python/42_BDF_Bar.png" imageCaption =  ""%}

Using a four cylinder car, you can run nearly 10 miles more than using one with six cylinders.

</center>

For the vertical bar chart, we chose the top 20 cars ranked descendingly for most miles per gallon:
<br><br>
<center>

{% include images/image.html imagePath = "../assets/images/img_blog/Python/43_BDF_BarH.png" imageCaption =  ""%}
Top 20 Cars for Most Miles Per Gallon
</center>

## Comments on the Vertical Bar Plot

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

- There is a good recommendation on saturation (of the color of the bars), with "0.5" being a value that subjectively adds to the beauty of the plot
- The palette "Blues" contains a fine-tuned pattern of blue colors.
- The horizontal orientation is specified with 'h'
- The confidence interval (ci) was chosen to be about 1 sigma.

    
## Comments on the Horizontal Bar Plot


It might be of interest, which cars actually do provde the best miles per gallon ratio.

- As a vertial bar plot is a transposed horizontal bar plot, mind when defining x-value and y-value that the x-value must be a numerical one.
- As 300+ names hardly fit into a plot, the number of detail shown should be limited. Provided you use it in other places as well, you might want the number of entries used variable.

>
    df = df.sort_values(by=[xValue], ascending=False)
    number = 20
    df = df.head(number)

df[yValue] = df[yValue].str.capitalize()

>
    myPlot = sns.barplot(
            data=df,
            x=xValue, 
            y=yValue,         
            orient="h",
            edgecolor="k",
            palette="Blues_r",
            saturation=0.49,
            ci=None,
        )


- The horizontal orientation is specified with 'h'
- The palette "Blues_r" is the reversed palette, which in this case puts more emphasis (darker blue) to the 'winner' of this ranking.
- The grid lines were here altered to make it easier to extract the numerical value.
