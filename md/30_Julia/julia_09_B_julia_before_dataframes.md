---
layout: 30_julia
title: Julia Pre Dataframes
permalink: /julia_before_dataframes
---

# Julia - Pre Dataframes


## Text output to console
>
    println("Hello Julia")

In Julia, Strings are denoted by double quotation marks ("text")

>
    language = "Julia"
    println("Hello, ", language)


## String Operations

Strings are immutable. Hence, this does not work: 
>
    language[1] = "C"

Common  workaround for immutable Strings: New string composed of parts of old string

In Julia, "String concatenation is done with * in Julia, not + like in Python." (docs.julialang.org)

>
    stringConcat = "Language: " * language[1:end]
    println(stringConcat)


### Numbers

Implicit type definition by representative + Type conversion

>
    n = 5
    x = 7.7
    y = n * x
    myInt = convert(Int64, round(y, digits=0))
    println(myInt)
    println(typeof(language), typeof(n), typeof(y), typeof(myInt))


### Loops

Julia starts with 1
Python needs indent, Julia needs an 'end'

>
    for i in 1:4
    if i > 1
    println("Stop")
    break
    end
    println("Hello, Number $i")
    end

### Functions

In Julia, you define a function as a function

>
    function addOne(x)
        return x + 1
    end
    println(addOne(5)) # 6




