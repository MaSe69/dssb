---
layout: 20_python
title: Pandas | Create
permalink: /pandas_create_annotations

---
# Pandas Create Annotations

## Create

### Create a dataframe from an array

>
    df = pd.DataFrame(columns=["Col_R1", "Col_R2"], data=[arr1, arr2])

### Create a dataframe from a dictionary


## Read



## Download

### Download a dataframe from the internet

For making requests, we need to install and import the library [requests](https://pypi.org/project/requests/) .
For streaming the downloaded content into a dataframe, it helps to use the library [io](https://docs.python.org/3/library/io.html)

> 
    import pandas as pd
    import requests
    import io


At first, make the request to get the content from a specified URL. Mostly, the content is in utf8.  
Then, read the data into a dataframe 

>
    url2 ="https://raw.githubusercontent.com/vega/vega-datasets/master/data/co2-concentration.csv"
    req = requests.get(url2).content
    data = req.decode('utf8')
    df = pd.read_csv(io.StringIO(data))



## Merge dataframes