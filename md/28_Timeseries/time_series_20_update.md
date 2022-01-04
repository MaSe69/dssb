---
layout: 20_python
title: Time Series Updates
permalink: /time_series_updates
---

# Time Series - Updates

The (artificial) account data in the [Time Series Starter Example](time_series_starter) are used to compute an artificial 'profit'. 

Let's assume, it is August 2023 and we just got hold of the account data of July 2023. 

- How to efficiently add these data to the existing chart?


<br>
<center>
{% include images/image.html imagePath = "../assets/images/img_blog/img_altair/TimeseriesUpdates.png" imageCaption =  ""%}
<br><br><b>
Time series with an artificial profit and the task to add one more data point.
</b><br>
</center>
<br>

The raw data are only available as "one file per month". Each file contains the data of 3 accounts. The task for each month is to compute the profit using a simple equation, which shall be called here a 'recipe'. 
Such a recipe could be much more complex, e.g. using different weight factors or considering a varying sub-set of these accounts.


<br>
<center>
{% include images/image.html imagePath = "../assets/images/img_blog/Python/Files_for_timeseries_update.png" imageCaption =  ""%}
<br><br><b>
The number of files to be handled might give you a better idea of problem.
</b><br>
</center>
<br>