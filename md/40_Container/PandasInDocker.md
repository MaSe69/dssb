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
