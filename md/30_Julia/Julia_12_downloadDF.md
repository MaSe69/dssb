---
layout: 10_generic
title: Julia - Downloads
permalink: /julia_download

---
# Python - Download Dataframes from the Internet

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

At first, we make the request to get the content from a specified URL.
Mostly, the content is in utf8.  

>
    url = "https://raw.githubusercontent.com/nassarhuda/easy_data/master/programming_languages.csv"
    D = download(url, "programming_languages.csv")
    df = CSV.read(D, DataFrame)
    print(first(df,5))

### Save the csv-file to the local file system

Specify a name:

>
    filename = "programming_languages.csv"

If you want to use the name of this current file, you can get it from

>
    @__FILE__

>
    CSV.write(filename, df)
    println("\nFile wrtten to $filename")

If you want to use the current path, you can get it from 

>
    absPath = @__DIR__
    absPath = pwd()
    
println(absPath)
thisFile = @__FILE__
println("This File: $thisFile")


## CO2 Concentration