---
layout: 10_generic
title: Julia
permalink: /julia_gettingStarted
---

## Before Julia Installation

My recommendations:
- Setup a Linux Operation system, e.g. Ubuntu.
- For versioning, use Git.
- For installation, use apt-get or pip3.
- Use Visual Studio Code together with its Julia Extension.

All you need, you find on the web. My apologies to not be able to give details on these prerequisites. Also, such details outdate quickly. 

Having said that, I put some links here [Julia References](julia_references). 


## Julia Installation

Last update: June 2021

When you are on Ubuntu, you can install Julia easily

>
    sudo pip3 install julia

However, you do not have a possibility to change the version.
Moreover, Julia does currently not provide a one-liner for upgrade. You also might need to remove the old version first to get the new one working.

Recommended way is to download the bins and install them locally, for the respective link see [Julia References](julia_references).     

Check the version using 

>
    which Julia

On the command line, to enter the so-called REPL, type

>
    julia


You can take things from there with the plenty of documentation provided, see also [Julia References]( [Julia References](julia_references)).     

## Julia - "Language Specifics" 


### Packages

Julia comes with packages. 
In the REPL, type the bracket "]" to got to the package manager and your console looks like this

> 
    pkg>


In the package manager you can directly add packages using **add**

>
    pkg> add DataFrames

You can also check the status (or version) of a package 

>
    pkg> st DataFrames


### Special operators

Operator: "Broadcasting". Element-wise operation needs to be prefixed with a fullstop. 

>
    .


Operator: "Bang". Using this operator on an equation, the original is changed as well. 

> 
    !




## Julia - "Before Dataframe" 

Though the focus is on dataframes here, a very brief introduction should be provided on the topics between 'starting with Julia' as a programming language and starting with dataframes in Julia.

In fact, it might be easy to get lost on the way towards the dataframes. Here is what you might want to be aware of before starting with dataframes:

- [Julia - Before Dataframes](julia_before_dataframes)


As a point on this site is to help to switch between Python and Julia smoothly, I put a summary of some relevant differences in the context here:

- [Python vs. Julia - Before Dataframes](python_julia_before_dataframes)









