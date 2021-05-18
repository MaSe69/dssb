---
layout: 01_landing
title: Beautiful Dataframes
permalink: /index
---

# Beautiful Dataframes

Dataframes are great.<br>
Beautiful dataframes are even better, because they lead to many more insights!<br><br>
A beautiful dataframe is a technical dataframe containing specific data and shaped to perfection.

### About this site

You can find here an approach to 'think in dataframes', 
but you are welcome to just use it as an info source.

- For free, you find on this site plenty of knowledge for immediate benefit to your dataframes, like this [Pandas Cheat Sheet](Pandas_Cheat_Sheet)
- Technical documentation is mostly available [in many references](references), but scarce are resources to combine the pieces.
- New insights emerging from in real life projects are constantly added. 

## Focus on dataframes

The approach taken here is to focus on a dataframes as entity in its own right. 

Most approaches in data science seem to focus on the model. Models are fine, but they are here only seens as tools to describe the dataframe. 

### Comparing to other areas

Reportedly, a sculptor said: "The lion was inside the stone all the time. I just had to remove everything that did not look like it."
Similarly, the beautiful dataframe is in the data. All you have to do is to put the data into a dataframe and then operate on it until it becomes that beautiful dataframe.

When seeing a child drawing a few lines and dots on a paper, you might ask: "What is it?". The child might be bewildered, because the image seems to be so clear. Similarly, an experienced data scientists 'sees' structures in raw data. The difficulty is to make this structure visible to any interested person. Visualization in this sense is just a tool to point out clearly features of the dataframe.  

### Benefits of dataframe focused approach

- Focusing on dataframes, you can reach goals that might have looked out of scope for you so far.
- Shaping a dataframes can help you to look at familiar problems from new angles, and to come to surprising insights.
- Good skills in Dataframes make you more flexible when switching between most popular languages in data science: Python, Julia, R and more. 

### Benefits of beautiful dataframes

Creating a beautiful dataframe takes time and effort.
Time and effort are always limited. Hence, a beautiful dataframe is a bit of a luxury.

However, luxury is important. Luxury makes the owner feel more imporant. Luxury leeds to envy from competitors.

Similarly, if your business competitors get to know about your beautiful dataframes - describing your operations, your prospects or your profits - they might want to have access to it or to get to a similar or better ones, or all of it. 

### What is beauty for dataframes?

Beauty can be defined as the 'place to be'
Beauty deals with fundamental elements and their relationships to each others.
There are requirements towards these elements and towards their respective positioning.

There are other dimensions of importance, but we regard them here as independent from beauty.
These are 
- Being in control
- Simplicity

## Mastering dataframes

At first, let's cover the fundamental skill sets

- You can [create dataframes](pandas_createDF) yourself
- Can load existing data directly into a dataframe
- Operations on columns
- Operations on rows
- Merging with other dataframes 
- Working on subsets of a dataframe

A next step can include
- Extracting features within the dataframe, particularly using grouping
- Fitting models to (parts of) the dataframe

### Programming languages

The choice of programming language does matter.  
Certainly, there is a mutual understanding in the programming community about 'what is a dataframe and what is not'.
Fundamental operations on a dataframe, e.g. add or remove rows or columns, can be expected in any language.
Following the respective guideline of the language, the implementation of even these fundamental operations can be quite different, and hence time-consuming to learn.

A bit more advanced operations, e.g. transposing or inverting a dataframe, can be supported to various degrees.
Increasing the chain of operations and thus deepening the complexity of your program, you might increasingly worry about having chosen the right programming language.

## Beautiful dataframes

Fundamentally,  there must be an 'idea' of a dataframe.

- A dataframe on a school class shall contain all students of that class and their most important attributes.
- A dataframe for a bill of material shall contain all components.
- A dataframe on profits shall contain all revenues and all costs for a company, product or 'profit center'.

As for faces or landscapes, our brains constructs a representation of beauty, also for dataframes.<br>
We recognize a beautiful dataframe, when we see one. Any ugliness sticks out.

However, we need also a constructive checklist for beauty. 
- Authenticty (Identity)
- Relevance, comprehensiveness and potential for surprises
- Balance (Relationships)
- Readability and Appearance
- Consistency
- Robustness (Symmetry)

There are other important attributes of a dataframe, which are often mentioned.
However, they are not decisive with regards to beauty.
- Resource allocation (Performance)
- Security, Privacy, Accessibility

### Authenticity

If the sculptor has no clear vision of the lion to carve out, chances are slim of an outcome recognizable as an animal.

Authenticity often starts with giving things a unique and fitting name.

The problem with dataframes is to have a well established and reasonable practice to abbreviate any dataframe with "df".
Further, you might start with available data that are far away from the desired outcome.

As a remedy, at least the occasional dump as a csv-file should get the unique, fitting name. Adding a version, e.g. "_v0.23" indicates the closeness to the desired result.


### Relevance, comprehensiveness and potential for surprises

Data are meant to map reality.
Only a part of reality is decisive for the future.
Getting to this decisive - and hence relevant - part of reality is a non-trivial task.

Further, the data should be complex - or 'deep' - enough to be incomprehesible by just looking at them. 

For example, there is no point in adding or keeping data in the dataframe that is irrevant to its purpose.
You could add the color of cars to a dataframe on cars. However, if your purpose is to investigate fuel consumption over time, such information is not relevant. 

### Balance

A face is seldomly assessed as beautiful, if parts of it are disproportionate. A big nose and small ears hardly fit together.

Often, data are available in abundance on a specific part of the topic, but scarce on other parts.
It is tempting to keep all available data in one dataframe, rather than to 'balance' the various independent dimensions.


### Readability and Appearance

When looking at a new dataframe, you want to quickly grasp what it is all about.
Technically, dataframes make it not easy to describe purpose and content. There is typically so far no provisioning for meta data. 

Column names are the prominent place to convey information about the dataframe. Unfortunately, it can be time saving during coding to keep the column names short and limited to one word. Hence, column names tend to be rather void of meaning.
Well chosen column names, however, can be sufficient to make the purpose of the dataframe clear. 

Another issue here can be floats which tend to be rendered with a lot of decimals. Browsing through a csv-file partially filled with missing data and partially filled with such floats can be tiring.  

### Consistency

For digits, decide about one unit and stick to it. Convert other currencies e.g. to the chosen one for the dataframe.
For date and time, one and only one useful format and accuracy should be chosen.
For words, often the same meaning is covered by the different words. Long words should be trimmed without loosing semantics.

### Robustness (Symmetry)

Reportedly, a symmetric face, particularly for older persons, shows robustness against the odds of live.
Further, the sense of beauty is meant to increase when the impression of beautifulness persists over time. 

Similarly, once made beautiful, a dataframe should not loose its beauty over time. If a beautiful dataframe becomes popular, contributors tend to add all kind of data to it. 

Data is often time dependent. It gets outdated. Data kept in the dataframe might be misleading. New data that should have been included for comprehensiveness might be missing.

The identity of the dataframe shall be kept over time, so it remains clear which data should flow in and which data need to be kept out or need to be removed.

# Summary

Dataframes are well-established in the context of data science and [references](references) were given.

Here, the idea and the benefits of the concept of a 'beautiful dataframe' was discussed.
Fundamentally, this is a dataframe-centric approach. It promotes the dataframe from a 'transitional tool' on the way from data to a model, to an entity in its own right. It also leads to a constructive approach to improve data quality.

Possibly you might want now to see some examples and browse through the skill sets used.
