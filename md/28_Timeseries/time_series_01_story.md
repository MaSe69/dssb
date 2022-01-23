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

The examples worked out for the 'Time Series Story' include

- Fundamental time series - making use of Pandas and Altair, see [Time Series - Starter](time_series_starter)
- Rolling updates to time series, see [Time Series - Updates](time_series_updates)
- Fit a linear regression to model data and check with test data, see [Time Series - Linear Regression](time_series_regression)
- Fit a Logistics regression to model data and check with test data, see [Time Series - Logistics Regression](time_series_logistics)


Applying Pandas and Altair to time series is quite straightforward.

It is getting a bit more complex, when the time series is not 'immutable'. A particular strong use case is to add new data to an existing time series. Such an update of a time series can be done in more or less efficient ways.


## Data Science for Entrepreneurs

A particular application of time series is for entrepreneurs. For an established business, there are plenty of almost finished solutions available, which mostly need some configuration or enhancements. For a new business, however, a lot of flexibility is needed to get to the true business point, see this [Entrepreneur Story](entrepreneur_story).







## Out of Scope

A considerable area of research and tooling is dealing with adapting models to time series. This includes noise reduction, fitting, splines, etc.. <br>
Such modelling is typically computational intensive. Julia can be recommended as a language of choice for such topics. 


