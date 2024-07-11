---
layout: 20_python
title: Time Series - Single Dates
permalink: /time_series_single_dates
---

# Single dates

## String date conversions

Let's start with something easy. Dates only as strings. For use in Plotly or some other libraries for figures, it is sufficient to have the date as strings. No need to mess around with datetime to create figures with time series. Just strings (and numbers) are needed.

I found that I need two types of data formats:

- 20250717 (I call it: dense date)
- 2025-07-17 (I call it: date with hyphen)

Why these formats? 

Mainly because I like to sort columns or files which is easier when the sequence is year, month, day. I need the date with hyphen for creating figures. I rather like tho use the dense date for naming files. Also, typing the dense date is a bit quicker. 

Typically, I  start with the dense date and at some point in time I will need the date with hyphen. But sometimes, I end up with the date in hyphen and need the dense date. 
Hence, I wrote a conversion function. Both dates are in strings, which can be used here to check for the length of the string. 

Coding
>
    ### Input either dense date or date with hyphen
    ### Output: the other type
    def convertFormats(refDate):
        dlen = len(refDate)
        if dlen == 8:
            print("Convert dense to hyphen")
            myDateNewType = refDate[:4] + "-" + refDate[4:6] + "-" + refDate[6:]
        elif dlen == 10:
            print("Convert hyphen to dense")
            myDateNewType = refDate[:4] + refDate[5:7] + refDate[8:9]
        else:
            myDateNewType = refDate
        return myDateNewType


## Last day of a month

For the time series that I intend to create, the data points are of the previous month. I like to have the tick on the x-axis to make it clear, where exactly that month ends.

Technically, I feed the figure with the 'last day of the previous month'. For some use cases, I need the last day of a month not for the previous month, but for any other months.
Hence, I wrote a function that returns this date given any other date, e.g. now.

Libraries needed
>
    import calendar
    from datetime import datetime
    from dateutil.relativedelta import relativedelta

Coding

>
    ### Input a point in time in a month as string or datetime, e.g. now
    ### Input: number of months back or forth
    ### Output: last day of the previous month
    def getLastDateOfMonth(refDate, myMonths, para):
        if isinstance(refDate, str):
            print("Convert datetime to string")
            dateFormat = para["TimeFormat"]
            refDate = datetime.strptime(refDate, dateFormat)
        oneMonthBefore = refDate + relativedelta(months=myMonths)
        lastDay = calendar.monthrange(oneMonthBefore.year, oneMonthBefore.month)[1]
        lastDayPerviousMonth = datetime(oneMonthBefore.year, oneMonthBefore.month, lastDay).strftime(para["TimeFormat"])
        return lastDayPerviousMonth

Call
> 
    myMonths = -1
    ### reference date can be now or any specified date
    prevEndDate = getLastDateOfMonth(refDate, myMonths, para)