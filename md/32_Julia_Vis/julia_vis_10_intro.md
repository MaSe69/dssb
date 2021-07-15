---
layout: 30_julia
title: Julia  Visualization
permalink: /julia_visualization
---

# Julia Visualizations For Dataframes

The focus here are dataframes. Hence, the topic is to visualize a particular dataframe.
An integration between dataframes and the graphics solution is key. 


## Many solutions

For Julia, many packages are available for visualization.

In fact, there are so many possibilities for visualization that it is difficult to choose from.
After some investigation, my choice came down to 
- Plots
- Vegalite

Other solutions that I looked into but do not describe here include
- Gadfly
- Makie

Links to the official documentations are given in the [Julia Visualization References](julia_visualization_references).


## Discussion of the choice

### Plots

Plots provides basic plotting functionality. 
Sometimes, you just want to visualize some data points. Nothing fancy, just for your own understanding.
Then, Plots is a quick and intuitive solution. 

For a dataframe with columns x and y, a visualization is as easy as
>
    using Plots
    plot!(df.x, df.y)

However, Plots has limits that some other solution needs to fill. 


### Vegalite

Vegalite is a solution that is based on Vega which itself is based on d3. d3 in turn is reportedly an extremely powerful graphics solution. The pro argument is hence that Vegalite sits on top of a solution that probably fulfills any requirement. If Vegalite proofs to have limits, Vega might do the job, if not d3 might fill that gap - at the expense of increased complexity, but at least you are not stuck at a dead end after having spent a lot of time going down the road of learning a complex graphics solution.

Vegalite is further integrated with Queryverse. Queryverse is a kind of meta package that smoothens the interfaces between several components. Vegalite.jl is a package that enables to program in Julia style the Vegalite Json syntax.

Vegalite comes with a convenient data set in VegaDatasets.
It is quite minimalistic coding - compared to other solutions - to have the cars data set visualized as follows.

>
    using VegaLite, VegaDatasets
    dataset("cars") |>
    @vlplot(
        :point,
        x=:Horsepower,
        y=:Miles_per_Gallon,
    )

No dataframe is involved here, but a dataframe could be used as input instead.
