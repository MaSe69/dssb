---
layout: 20_python
title: Time Series Regression
permalink: /time_series_regression
---

# Time Series - Regression

The task here is to **assess a regression model using with test data**. Particularly for the use case when at the beginning of a month the data of the previous month are available.

The problem addressed here is to **compute the model only with the model data**. Further, the chart should clearly show which data belong to the model and which belong to the test.

<center>
<br>
{% include altairhtml/20_BDF_ALT/30_50_TS_Regression_Interactive.html %}
<br><br><b>
The Vega Cars dataset with interactive, multiple selection. Use SHFT+Click to select multiple items.
</b><br>
</center>
<br><br>


## Solution idea and some details 

### Create file with aggregated, monthly data

The solution here is essentially an extension of the previous example on [Time Series Update](time_series_updates).
The chart was re-used adding
- the regression
- a text chart to display a statistical parameter.


### Regression

For the regression, the library 'optimize.curve.fit' of Scipy was used. 
For details, please go to [Scipy - Optimize Curve Fit](https://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.curve_fit.html).

Clearly, the library has to be imported. This is the only import needed here for the regression.
>
    from scipy.optimize import curve_fit

The decisive call is to the function 'curve_fit'

>
    popt, pcov2 = curve_fit(LinearFunction, dfTL.X, dfTL.Y)

In this approach, you can freely define a function for the fit. For the linear fit, the function is quite simple.

>
    def LinearFunction(x, a0, a1):
        y = a0 + a1 * x
        return y


The fitting parameters can be obtained from the exported parameter of the optimization, i.e. 'popt'.

>
    fittingPara = {}
    fittingPara["a0"] = round(popt[0], 3)
    fittingPara["a1"] = round(popt[1], 3)   


You get to the forecast using these parameters.

>
    fRL[column] = LinearFunction(dfRL.XF, *popt)


Some statistical parameters are returned, e.g. the co-variance matrix. 
Unfortunately, the value of 'RSquared' (R2) is not returned and you have to compute it manually.
