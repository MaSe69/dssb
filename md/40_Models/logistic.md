---
layout: 20_python
title: Models
permalink: /logistic
---

# Logistic Function For Time series

In fact, there is nothing special here about time series, but a mapping from the time series to integers and then back to the time series. The point is to make these two mappings most efficiently and readable in the coding.

The Logistic function used here was coded as

> 
    y = M * (1 / (1 + np.exp(-s * X)))

with

>
    M = MaximumMarketSize
    s = Steepness (of the slope)


## Optimization

There are several optimization libraries available in Python which can be used for fitting a curve and particularly for fitting the Logistic function. Here, the library scipy is used.

>
    from scipy.optimize import curve_fit

The optimization can be optimized with both an initial set of parameters (p0) and boundaries for these parameters (bounds)-

>
    popt, pcov = curve_fit(LogisticsFunction, dfTL.X, dfTL.Y, p0=p0, bounds=bounds)

The parameters optimized (popt) are returned from the optimizer together with the parameter covariance (pcov).

## Handling the Time Series

Shortly, before handing over to the optimizer, the fore each row of the time series an integers is created.

>
    dfTL["X"] = np.arange(0, dfTL.shape[0], 1)

This slightly enhanced dataframe is handed over to the optimizer. 

As the date remains within this dataframe, that's all that needs to be done. The original time series remains in the data frame and is used for the X-Axis in the subsequent chart.


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

The Altair library was used to display as two separate lines the data and the curve. Both lines were concatenated to a chart. 

## Evaluating the model

The residuals can be computed and in this case "R squared" (R2) was 0.975.


## Models References

- [Logictic Distribution - Numpy](https://numpy.org/doc/stable/reference/random/generated/numpy.random.logistic.html)
- [Logictic Distribution - Scipy](https://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.curve_fit.html)
