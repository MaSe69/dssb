---
layout: 10_generic
title: Julia
permalink: /julia_gettingStarted
---

## Before Julia Installation



My recommendations:
- Setup a Linux Operation system, e.g. Ubuntu
- For versioning, use Git
- For installation, use apt-get or pip3

All you need, you find on the web. Some resources that I keep using on my [Julia References](julia_references)

My apologies to not be able to give details on these prerequisites. Also, such details outdate quickly. 

## Julia Installation

Last update: June 2021

When you are on Ubuntu, you can install Julia easily

>
    sudo pip3 install julia

However, you do not have a possibility to change the version.
Moreover, Julia does currently not provide a one-liner for upgrade. You also might need to remove the old version first to get the new one working.

Recommended way is to follow the instructions to 
[Download a specific Julia version](https://ferrolho.github.io/blog/2019-01-26/how-to-install-julia-on-ubuntu). 

Check the version using 

>
    which Julia

On the command line, to enter the so-called REPL, type

>
    julia

