# Kubernetes Introduction

Welcome to the Kubernetes repository! This project contains examples and manifests for various Kubernetes resources, helping you get started with different concepts and components of Kubernetes. Below is a brief introduction to Kubernetes and an overview of the directories in this repository.

## What is Kubernetes?

Kubernetes is an open-source container orchestration platform that automates deploying, scaling, and managing containerized applications. It groups containers into logical units for easy management and discovery and allows you to control how and where those containers run.

### Key Features:
- **Automatic binpacking**: Efficient resource allocation for containers.
- **Self-healing**: Restarts failed containers and replaces them when necessary.
- **Horizontal scaling**: Automatically scale your applications up or down.
- **Service discovery and load balancing**: Automatically distributes traffic across containers.
- **Automated rollouts and rollbacks**: Seamlessly roll out updates with minimal downtime.

## Repository Structure

This repository is divided into different sections, each corresponding to key Kubernetes concepts:

### 1. **daemonSet/**
This directory contains Kubernetes DaemonSet manifests. A DaemonSet ensures that a copy of a pod runs on all (or specific) nodes in the cluster. It's useful for running background services like log collectors or monitoring agents.

### 2. **deployments/**
This directory includes Deployment manifests. Deployments help you manage your application’s lifecycle, such as scaling your app, rolling out updates, and handling rollbacks. It ensures that a specified number of pods are always running.

### 3. **liveness/**
The `liveness` directory contains manifests to define liveness and readiness probes. These probes are used by Kubernetes to detect when a container is running correctly or when it needs to be restarted.

### 4. **pods/**
Here, you will find manifests related to individual pods. A pod is the smallest deployable unit in Kubernetes, typically consisting of one or more tightly coupled containers.

### 5. **policies/**
This directory contains policy-related configurations, including network policies and pod security policies. These policies allow you to control traffic flows and define security rules for your workloads.

### 6. **replicaSet/**
This section holds ReplicaSet manifests. A ReplicaSet ensures a specified number of pod replicas are running at any given time, providing high availability and fault tolerance.

### 7. **services/**
Here, you will find manifests defining Kubernetes Services. Services expose your application to the network, allowing communication between different parts of your application and external users.

## How to Use

To deploy any resource in Kubernetes, you can use `kubectl apply` command. For example:

```bash
kubectl apply -f deployments/webserver.yaml
```
