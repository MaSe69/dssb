## Python | Julia

Please find here my first attempt to list some fundamental operations on dataframes in both Python and Julia.


:construction: Sorry, not all content online. Working on it ... 


|  Category   | Python | Julia |
|-------------|--------|-------|
| Dataframe   | [Meta Data](pandas_df_ops#meta-data) | [Meta Data](julia_df_ops#meta-data) |
| Dataframe   | [Basic Arithmetics](pandas_df_ops#basic-arithmetics) | [Basic Arithmetics](julia_df_ops#basic-arithmetics)  |
| Dataframe   | [Transpose](pandas_df_ops#transpose) | [Transpose](julia_df_ops#transpose) |
| Slice + Merge  | [Copy](pandas_slice_merge#copy)  | [Copy](julia_slice_merge#copy)  | 
| Slice + Merge  | [Slice](pandas_slice_merge#slice)  | [Slice](julia_slice_merge#slice) |
| Slice + Merge  | [Merge](pandas_slice_merge#merge) | [Merge](julia_slice_merge#merge) |
| Columns   | [Basic Arithmetics On Columns](pandas_columns#basic-arithmetics-on-columns) | [Basic Arithmetics  On Columns](julia_columns#basic-arithmetics-on-columns)  |
| Columns     | [Rename columns](pandas_columns#rename)  | [Rename columns](julia_columns#rename) |
| Columns     | [Reorder columns](pandas_columns#reorder) | [Reorder columns](julia_columns#reorder) |
| Columns     | [Insert columns](pandas_columns#insert) | [Insert columns](julia_columns#insert) |
| Columns     | [Modify](pandas_columns#modify) | [Modify](julia_columns#modify) |
| Columns     | [Delete columns](pandas_columns#delete) | [Delete columns](julia_columns#delete) |
| Rows        | [Sort](pandas_rows#sort)   | [Sort](julia_rows#sort)  |
| Rows        | [Create](pandas_rows#create) | [Create](julia_rows#create) |
| Rows        | [Delete](pandas_rows#delete) | [Delete](julia_rows#delete)  |
| Group       | [Group](pandas_group#group) | [Group](julia_group#group) |


## Mastering Dataframes

Please consult official documentations for Python and Julia programming language: 
- [Python - Pandas (Dataframes)](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html)
- [Julia - Package on Dataframes](https://dataframes.juliadata.org/stable/)

<br>
In addition, you find on this site for free:

- A selection from all possibilities based on practical experience.
- Comments on best practices and potential traps.
- A comparison between Python and Julia dataframes, meant to switch more efficiently between these languages.

<br>
Please find the details on this site here

- [Dataframes in Python-Pandas](pandas)
- [Dataframes in Julia](julia_df)

---

## Focus on Dataframes

First of all, this site is particularly meant to express gratitude towards all the inventors and contributors in this area.<br>

<br>
This site has grown as a collection of my personal cheat sheets. Saving my time to look up powerful, but hard to remember syntax. It might also save your time and make it more fun working with dataframes.

[The references on a sub page](python_references) take care mention the individuals to which we owe the great tools used here. Without Wes McKinney and his outstanding book on 'Python for Data Analysis' this site here would certainly not exist.

The approach taken here is to focus on a dataframes as entity in its own right.
It is a dataframe-centric approach. Dataframes with data are the heroes of this show.

The dataframe here is also persisted as such. This is in contrast to a data analysis in which the data are dynamically retrieved from multiple data sources.

### Benefits of Dataframe Focused Approach

- Focusing on dataframes, you can reach goals that might have looked out of scope for you so far.
- Shaping a dataframes can help you to look at familiar problems from new angles, and to come to surprising insights.
- Good skills in Dataframes make you more flexible when switching between most popular languages in data science: Python, Julia, R and more. 


### Out of Scope

Out-of-scope are the topics 'before' and 'after' the dataframe of a typical life cycle in data science.
This focus on dataframe excludes fundamental programming skills in any of the languages, and the many little helpers commonly used, e.g. Numpy.
Many approaches in data science focus on models, from regression to deep learning in AI. Models are fine, but this site focuses on dataframes. Nevertheless, something about dataframes can also be demonstrated when applying [models](models).

The choice of programming language does matter.  
Certainly, there is a mutual understanding in the programming community about 'what is a dataframe and what is not'.
Fundamental operations on a dataframe, e.g. add or remove rows or columns, can be expected in any language.
Following the respective guideline of the language, the implementation of even these fundamental operations can be quite different, and hence time-consuming to learn.

A bit more advanced operations, e.g. transposing or inverting a dataframe, can be supported to various degrees.
Increasing the chain of operations and thus deepening the complexity of your program, you might increasingly worry about having chosen the right programming language.

### Why more than one programming language?

If a dataframe is an idea, it needs to be independent of the implementation in a specific programming language.<br>
Programming languages in practice restrict by their intrinsic philosophy or available tooling.
Comparing the implementation in at least two languages is necessary to get closer to the 'true  nature' of dataframes. 

