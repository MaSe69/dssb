---
layout: 10_topic
title: Pandas - Downloads
permalink: /pandas_download

---
# Python - Download Dataframes from the Internet

### Requested libraries

For making requests, we need to install and import the library [requests](https://pypi.org/project/requests/) .
For streaming the downloaded content into a dataframe, it helps to use the library [io](https://docs.python.org/3/library/io.html)

> 
    import pandas as pd
    import requests
    import io

### First example: Some Programming Languages

At first, we make the request to get the content from a specified URL.
Mostly, the content is in utf8.  

>
    url = "https://raw.githubusercontent.com/nassarhuda/easy_data/master/programming_languages.csv"
    req = requests.get(url).content
    data = req.decode('utf8')

Then, we read the data into a dataframe - and check its first rows. 

>    
    df = pd.read_csv(io.StringIO(data))
    df.head(5)    

This example is actually from a great Julia tutorial.

### Second example: CO2 Concentration

Vega is graphics package commonly used with Julia. It also provides data, for the sake of its visualization.
It can also be downloaded with Python, of course:

>
    url2 ="https://raw.githubusercontent.com/vega/vega-datasets/master/data/co2-concentration.csv"
    req = requests.get(url2).content
    data = req.decode('utf8')
    df = pd.read_csv(io.StringIO(data))
    df.head(5)


