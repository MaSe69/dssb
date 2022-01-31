---
layout: 20_python
title: Categorization Story
permalink: /cat_story
---


# Categorization Story

In this story on categorization, you get some details on how to apply Pandas and Altair to discrete problems.

Interestingly, new words are common in this context for things that have existed before:
- value and target (= x- and y-values)
- label ( = y-value)
- trained model (= model with fitted parameters)
- 'hot encoding' (= values are binary, 0 or 1)
- 'confusion matrix' (= counting how often the model predicted correctly or did not)


## Examples

### Iris Data Set

The standard data used in this context are 3 kind of flowers that can be separated by specific lengths.<br>
You can find this model in many, many places.


### Dedicated Data Set Here

Using the dataframe skills on this site, it is easy to create own data.
It is not so easy to create a data set though that makes some real-world sense and can be used in all categorization models.

[Dedicated Data Set](cat_data_set) - First names, some attributes and a target value.



## Unsupervised models


### K-Means
 
K-Means is meant to be the simplest unsupervised model. You can use it to get a first idea, when you have not sufficient knowledge on the underlying target structure.


[K-Means](cat_kmeans) - 



## Supervised models

In supervised models, for a meaningful data set. you know both, the x-value and the y-value. 
After having fitted the parameters, you can use the model to estimate y given x.
(This is the same as done in regression for time series, but it sounds much more fancy.)


### Decision Tree

A decision tree might be the easiest starting point in such discrete problems. (Can it start easier than one Yes/No decision?)
Complexity can be raised, though, by adding more Yes/No decisions. Each such decision is commonly called a 'node'. From each node, two branches lead to either the next nodes or a result. 
"The paths from root to leaf represent classification rules."

[Decision Tree](cat_decision_tree) - This is my best example so far: First Names and athletic results - given some discrete parameters.


### Random Forest

As a model based on a decision tree is decisively influenced by the first decision taken, it is advisable to use an approach that uses a lot of such trees, i.e. a forest.

[Random Forest](cat_random_forest) - 


### Confusion Matrix

[Confusion Matrix](cat_confusion_matrix) - Illustration of the correctly and the incorrectly predicted values.



## Out of Scope

Categorization is typically a topic on the path to artificial neurological networks, also titled as 'artificial intelligence (AI)' or 'machine learning (ML)'.
Typical for such networks are the huge number of parameters that need to be fitted. This computational load leads to both dedicated hardware (e.g. GPU) and dedicated software.
Python is still an appropriate language with even superior features on the topics dealt with here. Python though was not invented to solve the problems that come specific with AI. 

My advice hence is to switch to another language for AI, and obviously, my language of choice would be Julia.
Some of the content on this website is meant to make this transition from Python to Julia less time consuming. 


## References for Categorization

- [Tutorial on Decision-Trees - YouTube](https://github.com/codebasics/py/blob/master/ML/13_kmeans/13_kmeans_tutorial.ipynb)
- [Wikipedia on Decision Trees](https://github.com/codebasics/py/blob/master/ML/13_kmeans/13_kmeans_tutorial.ipynb)
- [Tutorial on Kaggle on Decision Trees](https://www.kaggle.com/faressayah/decision-trees-random-forest-for-beginners#1.-Decision-Tree)
- [Scikit-Learn on K-Means](https://scikit-learn.org/stable/modules/clustering.html#k-means)
- [Confusion Matrix with Altair by Soren Laursen](https://towardsdatascience.com/the-confusion-matrix-visualized-e778584c8834)


