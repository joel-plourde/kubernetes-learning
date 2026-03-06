# Kubernetes Voting App Deployment

This repository documents my deployment of the classic Kubernetes Voting App as part of my Kubernetes learning journey on KodeKloud.

The goal of this project was to practice deploying and debugging a multi-service application inside a Kubernetes cluster.

The application was deployed locally using **Minikube** and managed with **kubectl** from my **terminal**.

## Application Architecture

The voting application consists of several microservices running inside Kubernetes.

* **Vote:**  Frontend web application where users submit their vote.

* **Redis:** Temporary datastore that queues incoming votes.

* **Worker:** Background service that processes votes and stores them in the database.

* **PostgreSQL:** Persistent database storing vote results.

* **Result:** Web application displaying the aggregated results.

## Kubernetes Resources

The application uses several Kubernetes components.

* Deployments
* Pods
* Services
* NodePort and ClusterIP networking
* ReplicaSets

Example cluster state:

```bash
kubectl get all
```

This shows all running components including pods, services, deployments, and replicasets.

## Accessing the Application Locally

Since this cluster runs on **Minikube using the Docker driver on macOS**, the easiest way to access the services is using the `minikube service` command.

Vote application:

```bash
minikube service vote --url -p jojo-homelab
```

Result application:

```bash
minikube service result --url -p jojo-homelab
```

Example output:

```
http://127.0.0.1:56736
http://127.0.0.1:56772
```

Opening these URLs in a browser allows interaction with the application locally.

Note: Because the Docker driver is used on macOS, the terminal session must remain open while the service tunnel is active.

## Useful Debug Commands

List running pods:

```bash
kubectl get pods
```

List deployments:

```bash
kubectl get deployments
```

List ReplicaSets:

```bash
kubectl get replicasets
```

List services:

```bash
kubectl get services
```

## Environment

* macOS
* Minikube
* Docker Desktop driver
* kubectl
* Warp terminal

## Part of My Kubernetes Learning Journey

More projects and experiments are available in my homelab organization.

https://github.com/jojo-homelab
