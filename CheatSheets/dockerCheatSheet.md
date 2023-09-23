---
title: My Docker Cheat Sheet
---

* TOC
{:toc}

# Containers

## Run Containers

Docker run reference see: [Docker run reference](https://docs.docker.com/engine/reference/run/)

### Non-interactive mode

#### Run New Container

`docker run <image name>` 

#### Run Existing Container

`docker start <container id>`

### Run in Interactive Mode

#### Run New Container

`docker run -it <image name>` 

#### Run Existing Container

`docker start -ai <container id>`

## Filter Containers

### Show Containers Filtered by Image Name

`docker ps -a --filter 'ancestor=<image name>' `

## Cleanup Containers

### Remove all containers

 `docker rm $(docker ps -aq)`

### Remove all containers from a specific image

`docker rm $(docker ps -aq --filter 'ancestor=<image name>' --filter 'status=exited')`

# Images

TBD
