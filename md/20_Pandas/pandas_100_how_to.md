---
layout: 20_python
title: Pandas How do I
permalink: /pandas_how_do_I

---
# Pandas - How do I ...?

This page is meant as my personal favorites to get started with Pandas. 
Please consult the [Official Pandas documentation](https://pandas.pydata.org/docs/user_guide/index.html#user-guide) for a comprehensive overview.

Obviously, you need to import Pandas
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


How do I get column names and change them?
>
    myColumnNames = list(df.columns)
    myColumnNames[3] = "Score_4"
    df.columns = myColumnNames

How do I re-arrange columns?
>
    myNewColumnsOrder = myColumnNames.copy()
    myNewColumnsOrder[1] = myColumnNames[3]
    myNewColumnsOrder[3] = myColumnNames[1]
    df = df[myNewColumnsOrder]

How do I reverse the column order?        
>
    df = df.set_index("Name")
    myColumnNames = list(df.columns)
    myReversedColumnNames = myColumnNames[::-1]
    df = df[myReversedColumnNames]
    df = df.reset_index()

How do I add a column with the sum?
>
    df = df.set_index("Name")
    df["Sum"] = df.sum(axis=1)
    df = df.reset_index()

How do I remove a specific column?
>
    df = df.drop(columns="Sum")    

How do I keep specific columns?
>
    keepColumns = ["Score_3", "Score_4"]
    dfReduced = df[keepColumns]

How do I keep columns at specific positions?
>
    df = df.set_index("Name")
    dfReduced = df.iloc[:, 1:3]
    dfReduced = dfReduced.reset_index()


How do I add a column with random numbers?
>
    import numpy as np
    np.random.seed(0)
    df["RandomInt"] = np.random.randint(170, 190, (1, df.shape[0])).tolist()[0]
    df["RandomUniform"] = np.random.uniform(
        low=170, high=190, size=(1, df.shape[0])
    ).tolist()[0]


How do I replace a value?
>
    df.Name = df.Name.str.replace("Jack", "John")
    df.Name = df.Name.str.replace("John", "Jack")

How do I add a column B based on condition in column A?
>
    df.loc[df["Score_4"] >= 20, ["Comment"]] = "Well done!"
    df.loc[df["Score_4"] < 20, ["Comment"]] = "Try again!"    


## How do I work with rows on a Pandas dataframe?

 How do I append a row?
 >
    df = df.set_index("Name")
    df.loc["David"] = df.loc["Jack"].copy()
    df = df.reset_index()

How do I sort by specified columns in various directions?
>
    sortColumns = ["Score_3", "Score_4"]
    directions = [True, False]
    df = df.sort_values(by=sortColumns, ascending=directions)

How do I delete a specific row?
>
    dfReduced = df.drop(df[df.Name == "David"].index)


How do I continue on a subset of rows?
>
    dfReduced = df.iloc[1:3, :]


How do I filter for specific conditions?
>
    dfFilter = df[df.Score_4 > 20]
    dfFilter = df[df.Name.str.contains("i")]

How do I check for uniqueness in a column?
>
    myColumnUniqueness = df.Name.is_unique

How do I remove duplicates?
>
    df = df.drop_duplicates(subset=["Name"], keep="first")
