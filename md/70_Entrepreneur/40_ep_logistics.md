---
layout: 20_python
title: Beautiful Dataframes
permalink: /ep_logistics
---


## Example

Costs have, unfortunately, no limit. Such a limit is needed for a meaningful example for the Logistic function.
A commonly used example are sales. A new product might be sold until the potential market is saturated. 

The number of sales per month is modelled using the Logistic function and the parameters listed below. Then, a bit of noise was added. 

### Parameter for Optimizing the fit to the Logistic function

The parameter used for the modeling is always the top one of the tripples below. The subsequent parameter are the lower (*_L) and upper (*_U) bounds for the optimization.

>
    - MaximumMarketSize_M = 1000
    - MaximumMarketSize_M_L = 500
    - MaximumMarketSize_M_U = 2000

>
    - Steepness_s = 0.5
    - Steepness_s_L = 0
    - Steepness_s_U = 1

>
    - Offset_cX = 6.83
    - Offset_cX_L = 0
    - Offset_cX_U = 16

>
    - Offset_cY = 100
    - Offset_cY_L = 20
    - Offset_cY_U = 180

The modelled sales data (using a Logistic function) were fitted by the Logistic function and unsurprisingly show a good fit to the fit. 

<center>
{% include images/image.html imagePath = "../assets/images/img_blog/img_altair/M_17_Regr_Logistics_Only.png" imageCaption =  ""%}
</center>




