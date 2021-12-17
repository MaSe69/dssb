---
layout: 26_altair
title: Altair Chart
permalink: /altair_details
---

# Altair Details

This is about working out the details of information more clearly.

### Modify the color palette

If you do not want to use the standard palette, you can use one of the many palettes available for Vegalite.

>
    alt.Color('Origin',
        scale=alt.Scale(scheme='tableau10'),   
    ),


### Set specific colors

Sometimes, you want to set specific colors. For instance, profits shall be green and losses red.

>
    alt.Color('Origin',
        scale={"range": [blue","red", "green"] 
        ]   
    )

You might want to pick colors from existing, color palettes.


### Set specific shapes

When using shapes, you can also set shapes.

>
    alt.Shape('Cylinders', 
        scale=alt.Scale(range=['triangle-left','square', 'triangle-left','circle', 'cross'])
    ),


    