---
layout: 20_python
title: Pandas How do I
permalink: /pandas_how_do_I

---
# Pandas - How do I?

Certainly, you need to import Pandas
>
    import pandas as pd

## How do I get a Pandas dataframe?

How do I create a dataframe from arrays?

>
    myColumns = ["Name", "Score_1"]
    list1 = ["Jack", 188]
    list2 = ["Olivia", 177]
    df = pd.DataFrame(columns=myColumns, data=[list1, list2])


How do I use example data from the Vega dataset for a Pandas dataframe?
>
    from vega_datasets import data
    df = data.cars()

How do I download tabular data from the internet into a dataframe?

>
    import requests
    import io
    url = "https://raw.githubusercontent.com/vega/vega-datasets/master/data/weather.csv"
    req = requests.get(url).content
    data = req.decode("utf8")
    df = pd.read_csv(io.StringIO(data))


How do I download tabular data from Wikipedia into a dataframe?
>
    import wikipedia as wp
    html = wp.page("List_of_video_games_considered_the_best").html().encode("UTF-8")
    df = pd.read_html(html)[1]


How do I read from a csv-file - and restrict rows and columns?
>
    df = pd.read_csv(filepath, skiprows=10, skipfooter=11, usecols=myUseCols)    


How do I save a Pandas dataframe as csv-file - and specify the separators between the columns?
>
    df.to_csv(filepath, sep=';')  


## How do I work with columns on a Pandas dataframe?


How do I add a column to the end of a Pandas dataframe?
>
    df["Score_2"] = [12, 24]

How do I insert a column at a specified position to a Pandas dataframe?
>
    df.insert(2, "Score_4", [21, 20])    

How do I rename a specific column?
>
    df = df.rename(columns={"Score_4": "Score_3"})









