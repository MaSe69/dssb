---
layout: 10_topic
title: Julia - Downloads
permalink: /julia_downloads

---
# Python - Download Dataframes from the Internet

> 
    using DataFrames
    using CSV


>
    df = CSV.read(P, DataFrame)
    first(df,5)   


>
    filename = "pl_year.csv"
    CSV.write(filename, df);



## CO2 Concentration

>
    url ="https://raw.githubusercontent.com/vega/vega-datasets/master/data/co2-concentration.csv"
    D = download(url, "co2.csv")

>
    df = CSV.read(D, DataFrame)
    first(df,5)    

