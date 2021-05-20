---
layout: 10_topic
title: Pandas - Downloads
permalink: /pandas_downloads

---
# Python - Download Dataframes from the Internet

> 
    import pandas as pd
    import requests
    import io


>
    url = "https://raw.githubusercontent.com/nassarhuda/easy_data/master/programming_languages.csv"
    req = requests.get(url).content
    data = req.decode('utf8')
    df = pd.read_csv(io.StringIO(data))
    df.head(5)    


## CO2 Concentration

>
    url2 ="https://raw.githubusercontent.com/vega/vega-datasets/master/data/co2-concentration.csv"
    req = requests.get(url2).content
    data = req.decode('utf8')
    df = pd.read_csv(io.StringIO(data))
    df.head(5)


