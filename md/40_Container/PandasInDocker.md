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



## Reading a local data file

Copy the data, e.g. a csv-file to the work directory.
If you copy everything anyway, you don't have to change the dockerfile. Just for sake of clarity here, it is necessary have a copy of the data in the work directory of your container.

Dockerfile
>
    COPY myData.csv ./usr/app/src

Then, you can access the file from within the container.

>
    df = pd.read_csv("myData.csv")


An obvious disadvantage of this method is the need to re-build the complete container every time the data change.


## Using a mounted volume

The recommended way to provide data to a container is to use a mounted volume.
In practice, this is easily done by adding an option when running the container. As I use a small script anyway, this is a one time effort to program. 

>
    import pandas as pd
    print("Pandas in a Docker container reading from a mounted volume")
    df = pd.read_csv("/app/data/myDataOnAMountedVolume.csv")
    print(df)


The dockerfile remains essentially unchanged
Dockerfile
>
    FROM python:3-alpine3.18
    WORKDIR /usr/app/src
    COPY requirements.txt /usr/app/src/
    RUN pip install --no-cache-dir -r requirements.txt
    COPY . /usr/app/src
    CMD ["python3", "mountedvolume.py"]


The important part is to add the option -v and both paths when running the container. The two parts are separated by a colon ":". The first part is the full path (of the folder only) to the location of the csv-file. The second part is the path inside the container.

Running the container from the command line
>
    docker run --rm -v <fullPathOnMyVMToTheProgram>/app/data:/app/data mountedvolume    

Now, you can change the data in the csv-File. Without re-building the container, you get the updated data as output when running the container.

## Conclusion

That's it essentially. Now you can program in using Pandas - or migrate exiting coding using Pandas to - a container. Once done, you can benefit from all the benefits of running in a container. These benefits are in particular to run 'almost anywhere' nowadays. If it runs on your machine, it should run on any platform that supports containers.
Based on this feature, you can profit from much short development cycles when developing locally and deploying afterwards for more public visibility or usage.

