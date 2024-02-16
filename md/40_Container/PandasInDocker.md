---
layout: 20_python
title: Pandas and Docker
permalink: /pandas_docker
---

# Docker Installation

[Docker Installation - Official page](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository)

>
    newgrp docker
    sudo usermod -aG docker <username>


## Useful Docker commands

>
    docker images   ### list images
    docker ps -a    ### list containers, all (running and stopped ones)

>
    docker build -t python_hello_world .    ### Build the image
    docker run --rm docker_hello_world      ### Create, start and delete the container from an image

## First Example

Python program named "docker_pandas.py"
>
    import pandas as pd
    print("Pandas running in a Docker container")
    df = pd.DataFrame(columns=["Col_0", "Col_1"])
    df.loc["Row_0"] = [11, 12]
    df.loc["Row_1"] = [21, 22]
    print(df)


Dockerfile
>
    FROM python:3-alpine3.18
    WORKDIR /usr/app/src
    COPY . ./
    RUN pip install -r requirements.txt
    CMD ["python3", "./docker_pandas.py"]

requirement.txt
>
    pandas==2.2.0


## First optimizations - Scripting

Programming typically means 'making incremental changes'. I do not want to download Pandas every time when I make a change in my Python coding. Hence, I use the caching or layering of Docker here.

> 
    FROM python:3-alpine3.18
    WORKDIR /usr/app/src
    COPY requirements.txt /usr/app/src
    RUN pip install --no-cache-dir -r requirements.txt
    COPY requirements.txt /usr/app/src/requirements.txt
    COPY . ./
    CMD ["python3", "docker_pandas.py"]


Further, I do not want to have more than the image of the current coding. Hence, I delete all old images before creating the new one.

A script to remove the old image(s) and build the new one.

>
    docker rmi -f $(docker images -aq)
    docker build -t mypandas .

Terminal output after some iterations:
>
    Pandas running in a Docker container
        Col_0  Col_1
    Row_0     88     12
    Row_1     21     99



