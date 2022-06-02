---
layout: default
title: Docker Part II
parent: 2021
nav_order: 8
---

# Docker Part II
{: .no_toc }

Presented on 11th April 2021 by [Jung](https://github.com/junglee1101)

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Dockerfile

----

- Docker builds custom images by reading the instructions from a `Dockerfile`. A `Dockerfile` is a text document that contains all the commands that assemble an image. Using `docker build` command, a user can automatically create a docker image that executes the custom command line insturctions successfully. 

Here are some common instructions to use in a dockerfile.

- **ADD** copies the files from a source on the host into the container’s own filesystem at the set destination.
- **CMD** can be used for executing a specific command within the container.
ENTRYPOINT sets a default application to be used every time a container is created with the image.
- **ENV** sets environment variables.
- **EXPOSE** associates a specific port to enable networking between the container and the outside world.
- **FROM** defines the base image used to start the build process.
- **RUN** is the central executing directive for Dockerfiles.
- **USER** sets the UID (or username) which is to run the container.
- **VOLUME** is used to enable access from the container to a directory on the host machine.
- **WORKDIR** sets the path where the command, defined with CMD, is to be executed.
- **LABEL** allows you to add a label to your docker image.

## Layered file system

----

![Docker container layers](container-layers.jpeg)
(src: [Docker's Docs](https://docs.docker.com/storage/storagedriver/))

- A Docker image consists of read-only layers each of which represents a Dockerfile insturction. The layer are stacked and each one is a delta of the changes from the previous layer. A user adds a new writable layer on top of the underlying layers. This is called the **container layer**. 

- **RUN**, **COPY**, **ADD** creates a layer. The other instructions will create intermediate layers and do not influence the size of your image. 


## Container Volume

----

- To avoid losing data when a user destroy a docker container, Docker provides **volumes** and **bind mounts** mechanisms for persisting data in a Docker container.

- Bind mounts mounts a file or directory on to your container from host machine, which can then reference via its absolute path. If a user wants a full control of the storage and plan on allowing other procsses besides Docker to access or modify the storage layer, then `bind mounts` is the right mechanism to use. 

- Bind mounts rely on the host machine's filesystem having a specific directory structure available. THe path has to be specify explicitly to the file or folder to place the storage. 

- To user bind mounts on a container, two flags options are available to use, `--mount` and `-v`. `--mount` is more verbose and explicit so `-v` is a shorthand for `--mount`. 

![bind-mounts-or-volume](types-of-mounts-volume.png)
(src: [Docker's Docs](https://docs.docker.com/storage/volumes/))

- Container Volume is the preferred method for persisting data generated by and used by Docker containers. 

- According to the Docker documentation, volume is the easiest way to begin persisting data in a Docker container. 

- Volumes are completely handled by Docker which gives several advantages over `bind mounts` as stated below. 

    - Storage is not coupled to the lifecycle of the container but instead exists outside of it. 
    - Easier to back up or migrate.
    - Can manage volumes by Docker CLI commands or the Docker API. 
    - Can be more safe to share among multiple containers. 
    - Volume drivers allow you to store on remote hosts or cloud providers. 
    - New volumes can have their content pre-populated by a container. 
    - Easy to attach to multiple running containers at the same time. 
    - The volumes don't increase the size of the Docker container using them. 


## Container Network

----

- One of powerful advantage of docker containers is that it can be connected to non-docker workloads. A docker network allow docker containers to talk to its host, other containers on the host or any other machines on or outside the host's network. `docker network` command provides subcommands such as `ls`, `create`, `attach` to configure networks and containers' relationship. 

- Docker's networking subsystem is pluggable using drivers. These are the drivers that exist by default. 

- `bridge`: The default network driver. It is usually used when an application run in standalone container that need to communicate.
- `host`: For standalone containers, remove network isolation between the container and the Docker host, and use the host's networking directly.
- `overlay`: connects multiple Docker daemons together and enable swarm services to communicate with each other. 
- `ipvlan`: This drivker gives total control over both IPv4 and IPv6 addressing. 
- `macvlan`: allow to assign a MAC address to a container, making it appear as a physical device on your network. 
- `none`: This disables all networking. 

## Docker Compose

----
- A tool for defining and running multi-container Docker applications. 

- Use an YAMl file to configure your application’s services 

- Define the application stack in a file, and easily enable someone else to contribute to the project

- Use a single command to spin everything up or tear it all down. 

- Usuaully defined in a file called `docker-compose.yml` and can spin up with command `docker-compose up -d` and `docker-compose down` to tear it down. 


## Resources 
1. [Docker docs](https://docs.docker.com/get-started/overview/)

2. [Docker commands](https://docs.docker.com/engine/reference/commandline/docker/)