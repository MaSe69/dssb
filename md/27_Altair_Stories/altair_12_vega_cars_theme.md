---
layout: 26_altair
title: Altair Themes
permalink: /vega_cars_theme
---

## Vega Cars Expanded - Theme

This is the result of the steps described below.


<center>
{% include images/image.html imagePath = "../assets/images/img_blog/img_altair/vegacarsexpanded_theme.png" imageCaption =  ""%}

<br><b>
The purpose of this graph with respect to content is the show the relationship between weight and fuel consumption. 
</b><br>

</center>



## Define and Use a Theme

Let's redo the previous example on [Vega Cars Expanded](vega_cars) using a theme.

### Using a ‘Theme’

You need to register and enable the theme such that it affects your chart.

<>
    from myTheme_file import myTheme
    alt.themes.register('myTheme', myTheme)
    alt.themes.enable('myTheme')

    

### Define a ‘Theme’

Using a theme can make your main coding much more concise. A theme is a collection of your choice of recurring chart configurations. You can further change the look of all your charts easily by just making the change once in your theme.

You can outsource the theme to an extra file. This extra file essentially contains a function. This function returns a ‘configuration’.

>
    def myTheme():
    ...
    return {
        'config': {
            "background": 'white', 
                    },
    }

However, you need to be careful about what to put into a theme, because you might not want all your chart to be identical. You can overwrite though a property set in the theme for your specific chart.




