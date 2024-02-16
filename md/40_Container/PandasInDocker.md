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



