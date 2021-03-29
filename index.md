---
layout: 01_landing
title: Data Science
permalink: /index
---
# Dataframes In Data Science 

Welcome,

this site is dedicated to data science.<br>
The focus is currently on **dataframes**. 

You might have come here from the main website 
- [drmaseway](https://www.drmaseway.com). 

Much of the code described here is available as Jupyter notebooks on Github
- [dataframes](https://github.com/MaSe69/dataframes/tree/master)


## What is a dataframe?

A dataframe might be defined as a matrix with column names and a row index.

Essentially, a dataframe is another word for the common table. It can also be modeled in a spreadsheet.  
<br/>
A dataframe - as it is a kind of table - is commonly used to store information.
Typically some different categories are stored in the columns.
The rows hold instances of an object in these categories. 

<br/>
The first and foremost reason to create a dataframe is to hold that information.
Reportedly, the Sumer invented writing some thousands of years ago particularly for the purpose to store the ownership of land. Such information can be stored as a dataframe. 
<br/><br/>
In business, transactions are typically stored in database tables, with each new transaction adding rows to their bottoms.
Before persisting the info to a database, it can be stored as a dataframe.
<br/><br/>
In some cases, the columns hold information on the time, e.g. Monday, Tuesday, ... .
Then, the dataframe holds a time series. As times evolves, new columns are typically added to the right end of the dataframe.
<br/><br/>
The position taken here is to assess a dataframe as a semantic entity. 
Sure, a dataframe is technically nothing else than a lot of tuples.
Similar to a sports car being nothing else than a collection of pieces of metal, glass and plastics.
<br/><br/>
In a given data community, members know 'their dataframes'. They would not be amused, if those formats suddenly change.
People get used to the names of columns and information being found at a specific position in that table.

The discussion on columns and rows might illustrate the conflict between a technical and a sematical view here. For a technical person, it does not matter which information is stored in columns and which in rows. After all, you just transpose the dataframe to have the same information but with columns and rows exchanged. For a semantical person, it can be crucial to a have the columns, the rows or both fixed. For many people, dates have to be in the columns and new transactions have to add new rows - anything else they might find too confusing. 


## Why are dataframes important for data science?

In my personal view, dataframes are the central piece of a data science curriculum.

There is a lot to be skilled at before you get the dataframes.
There is a lot to be waiting for you once you have sufficiently mastered dataframes.
<br/><br/>
Dataframes are somewhere 'in the middle' - depending on how much you care of the worlds before and after dataframes.
Hence, without dataframes, you are stuck in the world before. Sooner or later, you will feel the need to get familiar with dataframes. Better sooner than later. 


## Which language to use for dataframes?

In 2020+, there are 3 programming languages mainly in use for data science:
- R
- Python
- Julia

<br/><br/>
All three languages have 'dataframes'.
I am only familiar with Python and Julia. As Python's dataframe predates Julia's dataframe, it most likely has inspired its successor.
There are fundamental operations for a dataframe that are offered by these languages.
<br/><br/>
The focus here are these operations on a dataframe.
How to carry out these operations are the details which are described further down.
The main point is to be aware of these operations. 


# Working with Dataframes

After having given some context and hopefully some positive motivation on dataframes, you might want to get your hands on it. Possibly, you are searching for a particular solution.

Though we skip the world 'before dataframes', I compiled a notebook that lists a few particularities for each language.
I called it 'refresher' assuming that you are aware of the principles as such. Still, it might be worth refreshing the memory on the particularities of each language, e.g. that Python starts with 0 and Julia with 1.


## Create dataframes

Typically, dataframes already exist and you load them, work on them and finally save them - or their derivatives such as plots.
<br/><br/>
Occasionally, there is the need to create a new dataframe.
What people often like to do is to create an 'empty dataframe'. You might do so in a spreadsheet defining the columns and some rows - and leave the cells to be filled in later.
This simple start is not possible in Python, but Julia - thankfully - enabled it.
<br/><br/>
There are two ways, to create a dataframe
- from lists or arrays
- from a dictionary


### Save and read dataframes

Once you created a dataframe, you probably want to save it. Saving to disc as CSV-files comes as standard. 

More effort might be needed to get to the data. Reading from CSV-files directly into dataframes comes with a lot of options and best practices. 
Reading from an URL can be more cumbersome and might in practice require an intermediate step, but so far I always found a way to end up having the desired data in a dataframe.

For time series, it is possible to parse the column holding the time directly into the respective type. 
For more elaborate cases, a converter can be added to the read function that directly acts on the data on input.
For performance reasons, it is possible and recommendable to limit the number of rows or columns on input. 


## Data

A data scientist can't do his or her job without data.
Reportedly, there are more open-source data around than secret data. Good data are also needed to push algorithms and models further.
Kaggle seems to be an infinite source of data, though when dealing with most of the data there I found that I spent a lot of time until I got them into the requested shape.

Hence, I felt encouraged to put some data that are already available on the net also here. These data have already proven useful in this context and don't need much time to get started with. 


### Operate on the full dataframe

Often, a dataframe is a matrix embedded in columns and rows.
Then, it is meaningful to apply an operation to all cells of that matrix.
This saves looping over all columns or over all rows.

Practical examples include currency conversions or adding of fees. Some of these examples overlap with content of Linear Algebra. Certainly, this operation, e.g. multiplying with a real number, shall not be applied to the column headers or the row indices.

Some of the operation of this type are: 
- Multiplying a dataframe with a number.
- Adding or subtracting one dataframe from another dataframe.
- Transpose a dataframe
- Inverse a dataframe

For describing the full dataframe, there are some functions
- describe (to get some statistics
- shape (to get the number or columns or rows)

Handling missing values is also often possible on the full dataframe. It often comes down to fill all 'not a number' (NaN) with a more or less elaborate value.


### Operate on Columns

Sometimes, a dataframe is just not as it should be and some operations are needed to transform particularly its columns.

Some of the operation on columns are: 
- Rename the columns
- Re-order the columns
- Add columns (at the end)
- Insert columns at a specific position
- Delete columns

Slicing is a very powerful technique that also can be applied to columns.

Replacing values in existing columns is a very common task, particularly for data cleansing.
Conditional filling of values in columns is of great practical value. You want to insert a column and fill it depending on values in one or several other columns. 


### Operate on Rows

Sorting is one of the most frequent operations on rows. (There is rarely the need for sorting columns).

Some further operation on rows are: 
- selecting a subset on row by slicing or on condition
- deleting rows
- adding or copying rows


### Operate on Cells

Changing the cell (i,j) should be avoided when ever possible.
There is almost always a way to get around addressing a particular cell.
Almost always, but in rare cases, you really need to get to the one or other odd cell in a big dataframe, typically on given conditions. Though possible, it is cumbersome. 

## Second Steps on Dataframes: Aggregate, Merge

After having cleansed and wrangled one dataframe, you might want to continue to aggregate. 
After having soaked out all info from that one dataframe, you might continue with merging it with one or several other dataframes. Merging with other dataframes can also become a business of mass production, particularly for time series.


### Aggregation

Grouping is usually done in two steps. First, you group by one or several columns. Second, you apply a statistical operation, which might be as simple as a sum or a mean to that grouping. 

A revealed pattern in data science consists of 3 steps
- split
- operate (aggregate)
- merge


### Merging

For merging, obviously, you need some common ground. This could be a shared column. For time series, obviously a datetime object. If there is no semantic overlap, you can still merge on an index.
Rows and columns being technically the same, you can merge in both directions. You can expand the first dataframe by adding the second dataframe 'to the right' or 'to the bottom'.


## Language Specifics

Python and Julia offer all functionality described above. R presumably does so as well and probably many other languages, too. 

Julia's dataframe seems to have copied quite a bit of Python Pandas. The underlying philosophy of Julia seems to be, however, quite different from Python.

Python rather goes at length to make your program run through. Julia in contrast requires you to specify precisely what you want. In consequence, Julia's dataframes have diverted from Python's dataframes and this gap probably will continue to widen. With the high adoption of Python Pandas, it might be difficult for substantial changes. The Julia community might wish for more adoption but this felt moderate adoption also enable deprecations.

In any case, considerable detailed knowledge needs to be built up to become fluent in either Python or Julia dataframes. This can lead to a language lock-in.

A dictionary for dataframes in Julia and Python can be an essential bridge to cross from the one language to the other, when the context demands for other one.

First, you need to be assured that the requested functionality is there in the other language.
Then, you need to find the respective syntax.
Finally, some coding snippets and best practices can be helpful.


### Dataframes in Python (Pandas)

Please find here details of Dataframes in Python
- [Pandas](pandas).


### Dataframes in Julia (Dataframes.jl)

Please find here details of Dataframes in Julia
- [Dataframes.jl](dfjulia).


### Comparison of Dataframes in Python and Julia

Programming simultaneously in both langauge can be sometimes confusing. A cheat sheet to compare dataframes in Python and Julia might help:
- [Dataframes Comparison](dfcomparison).