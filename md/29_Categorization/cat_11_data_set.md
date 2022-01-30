---
layout: 20_python
title: Categorization
permalink: /cat_data_set
---


# Categorization Data Set

The data set presented here is used in the categorization models.

Some thoughts on it:
- Data privacy is an important topic in data science. The problem becomes more visible when names are introduced.
- The attributes and the target values shall be 'neutral'. 
- The data shall start simple, but be expanded into non-trivial complexity.

The concrete scenario:
- A training offer is made to a number of employees.
- An employee can accept this offer or decline it. 
- The offer here shall be 'a week of training'. So, the employee can either work as normal or to travel to another place to learn some new skills.

The task for a data scientist is to support the organization team for such a training set-up on questions like:
- How many training seats need to be offered?
- On which attributes does the acceptance of such a training depend?
- Would different types of training lead to more acceptance?

Available at the beginning are some data:
- The first names of the employees (for training purposes here from an official statistic. The first names are already unique.)
- The gender (male or female)
- The company affiliation measured in 3 steps.
- The answers of each employee to a question. 


<br>
<center>
<a href="time_series_tooltip">
{% include images/image.html imagePath = "../assets/images/img_blog/Python/BDF/30_BDF_CAT/Cat_Model_Data.png" imageCaption =  ""%}
</a>
<br><b>
Data Set manufactured to suit an introduction to a few categorization algorithms.
</b><br>
</center>
<br>




