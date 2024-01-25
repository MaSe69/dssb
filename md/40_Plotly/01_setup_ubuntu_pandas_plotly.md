---
layout: 20_python
title: Plotly Overview
permalink: /setup_ubuntu_pandas_plotly
---

# Ubuntu

As of January 2024, I am using Ubuntu of version 23.10 as you can download it from here [Ubuntu download official](https://ubuntu.com/download/desktop)

Once you have installed your IDE, e.g. Visual Studio Code, you might want to proceed with the package installations

# Environemnts

## How to install the capability to create environments?
>
    ### Install pip3
    sudo apt install python3-pip
    ### Install environment capability
    sudo apt install python3.11-venv

## How to create a specific environments?
>    
    ## Create a specific environment
    sudo python3 -m venv env

## How to activate your environment and grant it sufficient permission?
>
    ### Activate specific environment
    source env/bin/activate
    ### Add permissions to this environment
    sudo chown -R username:username env


## Installations required in the following

> 
     pip3 install pandas
     pip3 install plotly

Note: you cannot (should not) install using sudo.

You might want to check the version of Plotly
>
    ### On a terminal, enter
    >python3
        >>> import plotly
        >>> plotly.__version__

I will be using version  '5.18.0’


Note: All this info here can be found and it is better explained elsewhere. It is just collected here for time-saving purposes.








