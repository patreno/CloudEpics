---
title: KubeCtl Cheat Sheet
---

* TOC
{:toc}

# Pod details

## Show all pods

`kubectl get pod`

## Show pods in namespace

`kubectl get pod --namespace <namespace>`

# Service details

## Get all services

`kubectl get service`

## Get services in namespace

`kubectl get service --namespace <namespace>`

# Deployment

## Get all deployments

`kubectl get deployment`

## Get deployments in namespace

`kubectl get deployment --namespace <namespace>`

# Check logs

## Get logs of a pod

`kubectl logs <pod name> --namespace <namespace>`

## Get event log from a namespace

`kubectl get events --namespace <namespace> --sort-by=.metadata.creationTimestamp`

## Get deployment log from a namespace

`kubectl logs <deployment name> --namespace <namespace>`

'-f' can be added to follow log stream 

# Interactive Sessions

## Connect to cluster inside a container in interactive mode

`kubectl exec --namespace <namespace> -it <pod name> -- /bin/sh`

