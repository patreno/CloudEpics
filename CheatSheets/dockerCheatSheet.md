---
title: My Docker Cheat Sheet
---

* TOC
{:toc}

## Run Containers

Docker run reference see: [Docker run reference](https://docs.docker.com/engine/reference/run/)

### Run in Interactive Mode

#### Run New Container

`docker run -it <image name>` 

#### Run Existing Container

## Filter Containers

### Show Containers Filtered by Image Name

`docker ps -a --filter 'ancestor=<image name>' `

## Cleanup Containers

### Remove All Containers from a Specific Image

`docker rm $(docker ps -aq --filter 'ancestor=<image name>' --filter 'status=exited')`

# Images

TBD
