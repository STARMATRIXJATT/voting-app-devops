<<<<<<< HEAD
# Example Voting App

A simple distributed application running across multiple Docker containers.

## Getting started

Download [Docker Desktop](https://www.docker.com/products/docker-desktop) for Mac or Windows. [Docker Compose](https://docs.docker.com/compose) will be automatically installed. On Linux, make sure you have the latest version of [Compose](https://docs.docker.com/compose/install/).

This solution uses Python, Node.js, .NET, with Redis for messaging and Postgres for storage.

Run in this directory to build and run the app:

```shell
docker compose up
```

The `vote` app will be running at [http://localhost:8080](http://localhost:8080), and the `results` will be at [http://localhost:8081](http://localhost:8081).

Alternately, if you want to run it on a [Docker Swarm](https://docs.docker.com/engine/swarm/), first make sure you have a swarm. If you don't, run:

```shell
docker swarm init
```

Once you have your swarm, in this directory run:

```shell
docker stack deploy --compose-file docker-stack.yml vote
```

## Run the app in Kubernetes

The folder k8s-specifications contains the YAML specifications of the Voting App's services.

Run the following command to create the deployments and services. Note it will create these resources in your current namespace (`default` if you haven't changed it.)

```shell
kubectl create -f k8s-specifications/
```

The `vote` web app is then available on port 31000 on each host of the cluster, the `result` web app is available on port 31001.

To remove them, run:

```shell
kubectl delete -f k8s-specifications/
```

## Architecture

![Architecture diagram](architecture.excalidraw.png)

* A front-end web app in [Python](/vote) which lets you vote between two options
* A [Redis](https://hub.docker.com/_/redis/) which collects new votes
* A [.NET](/worker/) worker which consumes votes and stores them in…
* A [Postgres](https://hub.docker.com/_/postgres/) database backed by a Docker volume
* A [Node.js](/result) web app which shows the results of the voting in real time

## Notes

The voting application only accepts one vote per client browser. It does not register additional votes if a vote has already been submitted from a client.

This isn't an example of a properly architected perfectly designed distributed app... it's just a simple
example of the various types of pieces and languages you might see (queues, persistent data, etc), and how to
deal with them in Docker at a basic level.
=======
# voting-app-devops
CI/CD pipeline implementation for a Kubernetes-based Voting App using Azure DevOps for Continuous Integration and ArgoCD for Continuous Deployment.
# Voting App DevOps Pipeline

This repository contains the CI/CD pipeline setup for a Kubernetes-based Voting App. The CI pipeline is managed using **Azure DevOps Pipelines**, and the CD is handled via **ArgoCD**.

## 🔧 Tools Used:
- Azure DevOps Pipelines
- Docker
- Azure Container Registry (ACR)
- Kubernetes (AKS or any k8s cluster)
- ArgoCD
- GitOps workflow

## 🧩 What does this repo include?
- `azure-pipelines.yml`: Defines the CI pipeline for building & pushing Docker images.
- `scripts/updateK8sManifests.sh`: Bash script to automate image tag updates in Kubernetes manifests.
- `k8s-specifications/`: Directory containing Kubernetes deployment YAML files.
- `.dockerignore` & `Dockerfile` (for the Voting App)

## ⚙️ CI/CD Workflow:
1. **CI**: Azure DevOps pipeline triggers on commits to build Docker images and push them to ACR.
2. **CD**: ArgoCD monitors the repo and auto-syncs Kubernetes manifests to deploy new versions automatically.

## 🚀 Benefits:
- Automated builds & deployments
- Seamless integration with ACR & Kubernetes
- GitOps-driven deployment model
- Auto rollback and sync using ArgoCD

## 📂 Folder Structure:
├── azure-pipelines.yml ├── k8s-specifications/ │ └── vote-deployment.yaml ├── scripts/ │ └── updateK8sManifests.sh ├── vote/ │ └── Dockerfile
>>>>>>> be0ed41da713f511017723aced8a2d59bd0c254f
