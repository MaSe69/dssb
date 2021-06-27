---
layout: 20_python
title: Python Julia Comparison
permalink: /python_julia_comparison

---

# The dataframe as common ground

This dataframe-focused approach is based on the a common idea of 'dataframes' that holds true in various languages. 

The same (simple) data can be put to a dataframe in both langauges, see
- [Create a dataframe in Python](pandas_createDF)
- [Create a dataframe in Julia](julia_create)

On these data frames you can then carry out operations as outlined for dataframes.

In practice, this common ground opens up the possibility to switch between these languages.
You can store the data of a dataframe locally in one language and upload it again in the other language. If you happen to have a useful piece of coding or a library only in the one language, but the dataframe in the other language, this download/upload trick is a quick workaround.


# Differences - Relevant for the practical use with dataframes

## Language

An installation of Python tends to be easier than that of Julia. Using the Linux variant Ubuntu, it comes with the VM installation. Pandas is easily installed using pip3. For Julia, you need to have some kind of understanding of its packaging concept.

Python is a so-called interpreted language. Julia is a compiled language. 
We don't care here about the underlying techniques. Sorry. 

In practice for the developer, however, this difference has substantial consequences. In short, the benefits for the development phase are in favor of Python, but for the usage phase for Julia.

Python is forgiving and tries its best to guess what you wanted to do. The result might not be what you wanted, but that's your problem to check.

Julia is strict. You need to specify without ambiguity what you want it to do. 


### In Jupyter lab:

The forgivingness, robustness and development speed of Python also shows in Jupyter notebooks. You just select Python 3 as kernel and press run. As often as you like, in as many notebooks as you like. You might have your VS Code and Notebooks open and running them simultaneously.

With Julia, limit yourself. Think, before you re-start your kernel. Have patience.


### In VS Code

Development experience:
- In Python, you type coding, your run, you get the result - typically instantly.
- In Julia, you type coding, you run, you wait ... (compiling) ... then you get the result.

Usage experience:
- In Python, you run the program for a second time: it takes as long as the first time.
- In Julia, you run the program for the second time: Wow, now it's fast!


## Community for dataframes

Python is an older, general purpose language with a strong data science community. Compared to the overall universe of Python, this community might be relatively small.

Julia is a newer language with also a strong data science community. Within Julia the data science community apears to be relatively large or influencial or both.

When Python was created, much of the 2020+ computation environment did not exist, e.g. Cloud, shared respostories. Today's data abundance was far away. 

Hence, the latest features are rather to be expected to be added to Julia. Python might close gaps quickly, but if you want to stay at the edge of development, you need to invest in Julia. 


## Language features

Python starts counting at 0. Julia starts at 1. 



## Dataframe

Python is row based. Julia is column based.





