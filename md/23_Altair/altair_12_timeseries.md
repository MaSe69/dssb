---
layout: 20_python
title: Time Series
permalink: /timeseries
---

# Altair: Time Series - Lines

A standard use case in accounting are the values of accounts over time. You see here three accounts - A, B and C - with artificial data (incl. trend and Gaussian noise)

<center>
{% include images/image.html imagePath = "../assets/images/img_blog/img_altair/Timeseries.png" imageCaption =  ""%}
</center>

The chart is based on a theme such that all charts have the same background, grid line width or dash, etc..


### Define a 'Theme'

Using a theme can make your main coding much more concise. A theme is a collection of your choice of recurring chart conigurations.
You can further change the look of all your charts easily by just making the change once in your theme.

You can outsource the theme to an extra file. 
This extra file essentially contains a function. This function returs a 'configuration'. 

>
    def myTheme():
    ...
    return {
        'config': {
            "background": 'white', 
                    },
    }

However, you need to be careful about what to put into a theme, because you might not want all your chart to be identical. You can overwrite though a property set in the theme for your specific chart.


### Using a 'Theme'

You need to register and enable the theme such that it affects your chart.

>
    from myTheme_file import myTheme
    alt.themes.register('myTheme', myTheme)
    alt.themes.enable('myTheme')

### Long Format (melt)

I had created a file with time series before and had saved it as a csv file.
After reading the data into a dataframe, it needs to be converted from wide format to long format.

>
    df = df.reset_index().melt(id_vars="Month", var_name="Type", value_name="Measurement")

Altair does not accept the index to be set, thus reset the index during this melt operation.


### Height and Width

I sometimes want to change the ratio of the chart depending on the content. This setting worked quite well.

>
    chart = chart.properties(
        height=600,   
        width=900, 
        autosize=alt.AutoSizeParams(
            type='fit',
            contains='padding'
        ),
    )    


### Title and Subtitle

You can specify the text of the title and the subtitle in the chart properties. The formatting of them might mostly go to the theme.

>
    subtitle = ["Subtitle1", "Subtitle2"]
    title={
      "text": title, 
      "subtitle": subtitle,
    }, 

Great about subtitles: you can have more than one row!

Depending on the specific text for the chart, the title or subtitle often needs to be smaller or larger.

>
    myChart = myChart.configure_title(
        fontSize=26,
        subtitleFontSize=18,
    )    

Issue noted: When an automatically generated subtitle gets too long, the chart is not shown. 


### Format the X-Axis for Month

You can choose among different formats. yearmonth, for instance, displays both year and month.
The data must be in a suitable format, e.g. 2022-01-01. 
The axis can be scaled using a start date and an end date. 

>
    alt.X(
        'yearmonth(Month):T', 
        title="Month",
        scale=alt.Scale(domain=(startDate, endDate)),
        ),


### Format the Y-Axis

On the y-axis, most importantly you might set manually the scale and the number of ticks.

>
    alt.Y('Measurement:Q', 
            title="Y-Axis",
            axis=alt.Axis(tickCount=10),
            scale=alt.Scale(domain=(0, 2000)),
            ), 

### Format the Coloring

On the coloring, you might want to set the colors of your choice, e.g. you might want Account_A to be blue. You can enforce the sequence by sort.

>
    alt.Color('Type:O', title="Type", 
        sort=df.columns.values,
        scale={"range": [
            "blue"],
            "red"],
            "green"] 
            ]
            },
        ),   


The sorting is done along the columns of the dataframe.

### Format the Lines, Points

Formatting of the lines is directly done as parameters of the mark_line command.
You can set there the opacity level of the line, which softens the colors.<br>
You can change the lind from solid to dashed.<br>
You can configure a point for the data.

>
    mark_line(
        opacity=0.85,
        strokeDash=[4,2],
        point=alt.OverlayMarkDef(
            filled=False, 
            size=80, 
            fill='white',   
            ), 


