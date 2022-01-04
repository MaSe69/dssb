---
layout: 26_altair
title: Time Series Story
permalink: /time_series_story
---


# Time Series Story

In this story on time series, you get some details on how to apply Pandas and Altair when the x-axis is semantically time.

Time has some particular features:
- It is 'unique', it is 'ordered' and it continues to 'flow'.
- It has larger or smaller 'buckets'. 
- It is quite familiar to the reader of a chart.


These features imply consequences on presenting and programming time series.<br>
When you fail on the uniqueness or ordering, you end up with zig-zag lines that might go forward and backwards. <br>
Choosing an inappropriate granularity on the time scale can obscure the message or lead to performance issues.


## List of Examples

The examples worked out here include

- Fundamental time series - making use of Pandas and Altair, see [Time Series - Starter](time_series_starter)
- Rolling updates to time series, see [Time Series - Updates](time_series_updates)
- Regression to time series, see [Time Series - Regression](time_series_regression)

Applying Pandas and Altair to time series is quite straightforward.

It is getting a bit more complex, when the time series is not 'immutable'. A particular strong use case is to add new data to an existing time series. Such an update of a time series can be done in more or less efficient ways.


## Technical overview

Technically, there is the data type 'timestamp', which is sometimes useful. 
Altair adds great support for the x-axis. In particular, the tick labels are set in a meaningful manner. 
Adding, for instance, the year at the position of January on a multi-year x-axis is a little, but great feature.


## Out of Scope

A considerable area of research and tooling is dealing with adapting models to time series. This includes noise reduction, fitting, splines, etc.. <br>
Such modelling is typically computational intensive. Julia can be recommended as a language of choice for such topics. 


