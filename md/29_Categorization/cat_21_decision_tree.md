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



