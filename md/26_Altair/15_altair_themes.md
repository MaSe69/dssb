---
layout: 26_altair
title: Altair Themes
permalink: /altair_themes
---

## Themes 

### Define a ‘Theme’

Using a theme can make your main coding much more concise. A theme is a collection of your choice of recurring chart configurations. You can further change the look of all your charts easily by just making the change once in your theme.

You can outsource the theme to an extra file. This extra file essentially contains a function. This function returns a ‘configuration’.

    def myTheme():
    ...
    return {
        'config': {
            "background": 'white', 
                    },
    }

However, you need to be careful about what to put into a theme, because you might not want all your chart to be identical. You can overwrite though a property set in the theme for your specific chart.


### Using a ‘Theme’

You need to register and enable the theme such that it affects your chart.

    from myTheme_file import myTheme
    alt.themes.register('myTheme', myTheme)
    alt.themes.enable('myTheme')


