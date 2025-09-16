# Kubernetes First Deployment 

Welcome to my first Kubernetes deployment project! This repository contains configuration files and examples for deploying applications to a Kubernetes cluster.

##  Table of Contents

- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Deployment Instructions](#deployment-instructions)
- [Useful Commands](#useful-commands)
- [Troubleshooting](#troubleshooting)
- [Learning Resources](#learning-resources)
- [Contributing](#contributing)

## 🎯 Overview

This project demonstrates basic Kubernetes concepts including:
- **Namespaces** - Organizing and isolating cluster resources
- **Deployments** - Managing replicated application instances
- **Services** - Exposing applications within the cluster
- **Pods** - The smallest deployable units in Kubernetes

## 📚 Prerequisites

Before you begin, ensure you have the following installed:

- **Kubernetes Cluster** (minikube, kind, or cloud provider)
- **kubectl** - Kubernetes command-line tool
- **Docker** - Container runtime (for building images)
- **Git** - Version control

### Installing Prerequisites

#### Install kubectl
```bash
# On macOS
brew install kubectl

# On Ubuntu/Debian
sudo apt-get update && sudo apt-get install -y kubectl

# On Windows (using Chocolatey)
choco install kubernetes-cli
```

#### Install Minikube (for local development)
```bash
# On macOS
brew install minikube

# On Ubuntu/Debian
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

## 📁 Project Structure

```
.
├── deployment.yml           # Application deployment configuration
├── namespace.yml            # Kubernetes namespace definition
├── service.yml              # Service to expose the application
└── README.md                # This file
```

## 🚀 Getting Started

### 1. Clone the Repository
```bash
git clone https://github.com/DevNishantHub/Kubernates-first-deployment.git
cd Kubernates-first-deployment
```

### 2. Start Your Kubernetes Cluster
```bash
# If using minikube
minikube start

# Verify cluster is running
kubectl cluster-info
```

### 3. Check Cluster Status
```bash
kubectl get nodes
kubectl get pods --all-namespaces
```

## 🔧 Deployment Instructions

### Method 1: Using kubectl directly

1. **Create the namespace first:**
```bash
kubectl apply -f namespace.yml
```

2. **Deploy the application and service:**
```bash
kubectl apply -f deployment.yml
kubectl apply -f service.yml
```

3. **Verify the deployment:**
```bash
kubectl get namespaces
kubectl get deployments -n <your-namespace>
kubectl get pods -n <your-namespace>
kubectl get services -n <your-namespace>
```

4. **Access the application:**
```bash
# Get service details
kubectl get svc -n <your-namespace>

# Port-forward to localhost (replace with your service name and namespace)
kubectl port-forward -n <your-namespace> service/<service-name> 8080:80
```

### Method 2: Deploy all at once

1. **Deploy all resources:**
```bash
kubectl apply -f .
```

2. **Verify everything is running:**
```bash
kubectl get all -n <your-namespace>
```

## 📝 Useful Commands

### Basic Kubernetes Commands
```bash
# Get cluster information
kubectl cluster-info

# List all resources
kubectl get all

# Describe a specific resource
kubectl describe pod <pod-name>
kubectl describe service <service-name>

# View logs
kubectl logs <pod-name>
kubectl logs -f <pod-name>  # Follow logs

# Execute commands in a pod
kubectl exec -it <pod-name> -- /bin/bash

# Delete resources
kubectl delete -f .
kubectl delete -f deployment.yml
kubectl delete -f service.yml
kubectl delete -f namespace.yml
```

### Debugging Commands
```bash
# Check pod status and events
kubectl get pods -o wide
kubectl describe pod <pod-name>

# View cluster events
kubectl get events --sort-by=.metadata.creationTimestamp

# Check resource usage
kubectl top nodes
kubectl top pods
```

## 🔍 Troubleshooting

### Common Issues

#### 1. Pod Stuck in Pending State
```bash
kubectl describe pod <pod-name>
```
**Common causes:**
- Insufficient resources
- Image pull issues
- Node selector constraints

#### 2. Service Not Accessible
```bash
kubectl get endpoints
kubectl describe service <service-name>
```
**Common causes:**
- Incorrect selector labels
- Port configuration issues
- Service type mismatch

#### 3. Image Pull Errors
```bash
kubectl describe pod <pod-name>
```
**Common causes:**
- Incorrect image name or tag
- Registry authentication issues
- Network connectivity problems

### Helpful Debug Commands
```bash
# Check if services are running
kubectl get svc

# Verify endpoints
kubectl get endpoints

# Check ingress (if applicable)
kubectl get ingress

# Describe all resources in namespace
kubectl describe all
```

## 🎓 Learning Resources

### Official Documentation
- [Kubernetes Official Docs](https://kubernetes.io/docs/)
- [kubectl Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)

### Tutorials and Guides
- [Kubernetes Basics](https://kubernetes.io/docs/tutorials/kubernetes-basics/)
- [Learn Kubernetes](https://learnk8s.io/)
- [Kubernetes Academy](https://kubernetes.academy/)

### Practice Platforms
- [Play with Kubernetes](https://labs.play-with-k8s.com/)
- [Katacoda Kubernetes](https://katacoda.com/courses/kubernetes)

##
