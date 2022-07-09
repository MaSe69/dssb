---
layout: 20_python
title: Beautiful Dataframes
permalink: /beautiful_dataframes
---


# Beauty and Dataframes

**Beautiful dataframes** comprise the technical means of dataframes and their data of domain knowledge shaped to perfection.

### The Idea of Beauty in Other Areas

The point here is to apply the idea of beauty from other areas to dataframes.

Reportedly, a famous sculptor once said: "The lion was inside the stone all the time. I just had to remove everything that did not look like it."
Similarly, the beautiful dataframe is in the data. All you have to do is to put the data into a dataframe and then operate on it until it becomes that beautiful dataframe.

When seeing a child drawing a few lines and dots on a paper, you might ask: "What is it?". The child might be bewildered, because the image seems to be so clear. Similarly, an experienced data scientists 'sees' structures in raw data. The difficulty is to make this structure visible to any interested person. 

:chart_with_upwards_trend: [Visualization](python_visualization) in this sense is just a tool to point out clearly features of the dataframe.  

### What is Beauty?

:sunrise_over_mountains: Beauty can be defined as the 'place to be'. <br>
There is stability in beauty. A desire to preserve it as it is. <br>
Beauty deals with fundamental elements and their relationships to each other.
There are requirements towards these elements and towards their respective positioning.

There are other dimensions of importance, e.g. simplicity and 'being in control', but we regard them here as independent from beauty. A beautiful dataframe does not need to be simple, like a beautiful castle might not be simple. 

### Benefits of Beautiful Dataframes

Creating a beautiful dataframe takes time and effort.
Time and effort are always limited. Hence, a beautiful dataframe is a bit of a luxury.

However, luxury is important. Luxury makes the owner feel more important. Luxury leads to envy from competitors.

Imagine your business competitors to get to know of your beautiful dataframes - describing your operations or your profits or your plans  - they might want to have access to it or to get to a similar or better ones, or all of it. It would be more than just data, it would be a representation of your understanding of your world, of your actual and possible insights.


## Creating Beautiful Dataframes

Fundamentally,  there must be an 'idea' of a dataframe.

- A dataframe on a school class shall contain all students of that class and their most important attributes.
- A dataframe for a bill of material shall contain all components.
- A dataframe on profits shall contain all revenues and all costs for a company, product or 'profit center'.

As for faces or landscapes, our brains constructs a representation of beauty, also for dataframes.<br>
We recognize a beautiful dataframe, when we see one. Any ugliness sticks out.

However, we need also a constructive checklist for beauty. 
- Authenticity (Identity)
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


### Relevance and Comprehensiveness

Data are meant to map reality.
Only a part of reality is decisive for the future.
Getting to this decisive - and hence relevant - part of reality is a non-trivial task.
The data should be complex - or 'deep' - enough to hold surprising insights even for a domain expert.

Comprehensive coverage of the topic of interest is absolutely decisive! <br>
Particularly in the context of decision-making. 
You need to ensure that the data covers all relevant aspects. 


### Balance

A face is seldomly assessed as beautiful, if parts of it are disproportionate. A big nose and small ears hardly fit together.

Often, data are available in abundance on a specific part of the topic, but scarce on other parts.
It is tempting to keep all available data in one dataframe, rather than to 'balance' the various independent dimensions.

More advanced, you need to find the Eigen vectors of your topic to focus data gathering and analysis on them.


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
Further, the sense of beauty is meant to increase when the impression of beauty persists over time. 

Similarly, once made beautiful, a dataframe should not loose its beauty over time. If a beautiful dataframe becomes popular, contributors tend to add all kind of data to it. 

Data is often time dependent. It gets outdated. Data kept in the dataframe might be misleading. New data that should have been included for comprehensiveness might be missing.

The identity of the dataframe shall be kept over time, so it remains clear which data should flow in and which data need to be kept out or need to be removed.
