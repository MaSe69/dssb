---
layout: 20_python
title: Time Series - DF with Dates
permalink: /time_series_df_with_dates
---

# Dataframe with dates

When working with Pandas dataframes anyway, the question comes up, if the problem cannot be better solved using Pandas directly. There are a lot of datetime functions for dataframes. 

Hence, in principle there are two ways to solve some problems:

- A) Create the dates in step 1) and then use the dates in a dataframe in step 2)
- B) Create a dataframe in step 1) and then use the Pandas functions to create the dates. 

As usual, once you have a solution, you might suspect that the other possible way would have been better. Same with me here. I had solutions with the dataframe being created second, but then switched to solutions with the dataframe being created first.
There is an advantage of 'economies of scales in the context of figures, when first having the dataframe with the dates, because all figures then can have the same (optimized) layout. 
There are two separate use cases which I at first tried to handle with one function, before finally deciding to make two out of them:

- A dataframe having a fixed start date and end date, particularly the 12 months of a year
- A dataframe having n months back and m months forth, particularly 7 months back including the current 
month and one month to the future. 

For figures with labelled data points, there is a good reason to have one month more to the past and to the future, because the text is often truncated. For a time series, the value of most interest might not be printed in full, which can be very irritating.


## Dataframe for months with fixed start date and end date

The input is a start date and an end date. The output is a dataframe with a few columns for dates. As columns, I chose

- The date in string format
- The date in datetime format
- The name of the month

For my use cases, I do not have to care for response times. Hence, I can afford to compute more than I need and to keep only the needed columns. 

Note: You can easily make derivatives from these columns. If you do not need the day, just slice it away from the string column. Similarly, you can replace the last day of the month with any other day. 

Note: Both ends are included by default. Hence, the start date and the end date are in the first and the last rows of the dataframe. 

Reference: [https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.date_range.html](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.date_range.html)


## Dataframe for months going to the past and the future

Same as above, but the start date and the end date are computed within the function based on the following inputs:

- a reference date, e.g. now
- the number of months going back
- the number of months going forth

I do not need hours. Hence, I added to the data range function,  normalize=True. Without that, you get the milliseconds, because the "now" also had the milliseconds.
