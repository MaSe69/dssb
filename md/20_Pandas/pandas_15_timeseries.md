---
layout: 20_python
title: Pandas
permalink: /pandas_timeseries
---

## Timeseries

For timeseries, you can directly read the column holding the date or time into a datetime type.
A datetime can be used, for instance, to add a number of days. 

> 
    df = pd.read_csv(fullPathName, parse_dates=["Date"])

>
    from datetime import timedelta, date
    ...
    df["DatePlus"]= df.Date + timedelta(days=180)

