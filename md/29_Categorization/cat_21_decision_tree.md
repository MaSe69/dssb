---
layout: 20_python
title: Categorization
permalink: /cat_decision_tree
---


# Decision Tree

## Solution idea and some details 

 The algorithm 'decision tree' is here applied to the [categorization data set](cat_data_set) 

You see below the data set split into two parts: one part used for training the model, the other part used to test the model.


<br>
<center>
<a href="time_series_tooltip">
{% include images/image.html imagePath = "../assets/images/img_blog/Python/BDF/30_BDF_CAT/Cat_Model_Tree.png" imageCaption =  ""%}
</a>
<br><b>
Categorization Data Set
</b><br>
</center>
<br>


## Solution idea and some details 

### Splitting the data set
 
The library sklearn offers an effective and efficient way to split a dataframe into a part for training the model and another part for testing it. The fraction reserved for testing here was 40%. 

>
    from sklearn.model_selection import train_test_split
    dfT["Split"] = "T"


### Applying the model

The decisive lines of coding here are to create the model and to fit the training data. <br>
Afterwards, the a column in the main dataframe is added to hold the predicted values.

>
    myModel = tree.DecisionTreeClassifier()
    myFit = myModel.fit(df[inputCols], df[targetCols])
    ...
    df["Prediction"] = myModel.predict(df[inputCols])


### Quality of Model

A 'score' gives a first indication of the quality of the model.
The 'Gini' values can give you confidence about the distribution of the target values or put the distribution in doubt.

>
    myScore = myModel.score(df[inputCols], df[targetCols])
    giniValues = myFit.tree_.impurity

### Displaying the Decision Tree With Parameters

A nice, optional feature is to have the decision tree visualized. The library graphviz can help on the visualization.

>
    from sklearn.tree import export_graphviz
    from graphviz import Source