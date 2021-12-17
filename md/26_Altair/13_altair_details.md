---
layout: 20_python
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
        scale=alt.Scale(scheme='tableau10'),   
    ),

### Set specific colors

You can also set shapes.

alt.Shape('Cylinders', 
    scale=alt.Scale(range=['triangle-left','square', 'triangle-left','circle', 'cross'])
),
    