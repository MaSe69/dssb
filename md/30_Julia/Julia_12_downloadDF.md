---
layout: 10_generic
title: Julia - Downloads
permalink: /julia_download

---
# Julia - Download Dataframes from the Internet

## Installation

For a download to a CSV format, you need to install the package CSV.
In the package manager, add the package "CSV".

> 
    add CSV

At the top of your program, add

>
    using DataFrames
    using CSV

### First example: Some Programming Languages

At first, you make the request to get the content from a specified URL.

>
    url = "https://raw.githubusercontent.com/nassarhuda/easy_data/master/programming_languages.csv"
    D = download(url, "programming_languages.csv")

Then, you convert the download to a dataframe

>
    df = CSV.read(D, DataFrame)
    print(first(df,5))

The CSV functionality converted the data to a dataframe.

### Save the csv-file to the local file system

Specify a name:

>
    filename = "programming_languages.csv"

If you want to use the name of this current file, you can get it from

>
    @__FILE__

>
    CSV.write(filename, df)
    println("\nFile written to $filename")

If you want to use the current path, you can get it from 

>
    absPath = @__DIR__
    absPath = pwd()


### Example: Some CO2 - concentration

Just to make another example:

>   
    url2 ="https://raw.githubusercontent.com/vega/vega-datasets/master/data/co2-concentration.csv"
    D = download(url, "co2.csv")
    df = CSV.read(D, DataFrame)
    filename = "co2.csv"
    CSV.write(filename, df)
    println("\nFile written to $filename")

