# Task-5-Minikube

This project demonstrates deploying a web application on Minikube using Kubernetes.

## Prerequisites

### Install kubectl (Kubernetes CLI)

**macOS:**
```bash
brew install kubectl
```

**Linux:**
```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
```

**Windows:**
```bash
choco install kubernetes-cli
```

### Install Minikube

**macOS:**
```bash
brew install minikube
```

**Linux:**
```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

**Windows:**
```bash
choco install minikube
```

## Getting Started

### 1. Start Minikube

```bash
minikube start
```

### 2. Verify Cluster Status

```bash
kubectl cluster-info
kubectl get nodes
```

### 3. Apply Deployment Manifest

```bash
kubectl apply -f deployment.yaml
```

## Basic Kubernetes Commands

### View Pods

```bash
# List all pods
kubectl get pods

# Get detailed pod information
kubectl get pods -o wide

# Describe a specific pod
kubectl describe pod <pod-name>
```

### View Services

```bash
# List all services
kubectl get svc

# Get detailed service information
kubectl get svc -o wide
```

### Create a Service (if needed)

```bash
# Expose the deployment as a service
kubectl expose deployment webapp --type=NodePort --port=3000
```

### Port Forwarding

```bash
# Forward local port to pod
kubectl port-forward deployment/webapp 8080:3000
```

Then access the application at: `http://localhost:8080`

### Alternative: Using Minikube Service

```bash
# Open service in browser (if service exists)
minikube service webapp
```

## Useful Commands

### View Logs

```bash
# View pod logs
kubectl logs <pod-name>

# Follow logs in real-time
kubectl logs -f <pod-name>
```

### Delete Resources

```bash
# Delete deployment
kubectl delete deployment webapp

# Delete service
kubectl delete service webapp

# Delete using manifest file
kubectl delete -f deployment.yaml
```

### Stop Minikube

```bash
minikube stop
```

## Screenshots

![Minikube Setup](images/Screenshot%202025-08-11%20at%2011.01.35PM.png)

![Deployment Status](images/Screenshot%202025-08-15%20at%2012.34.06PM.png)

![Pod Information](images/Screenshot%202025-08-15%20at%2012.34.15PM.png)

![Service Access](images/Screenshot%202025-08-15%20at%2012.35.11PM.png)

## Application Details

- **Image**: `hatakekakashihk/frontend`
- **Port**: 3000
- **Replicas**: 1

## Troubleshooting

- If pods are not starting, check logs: `kubectl logs <pod-name>`
- Verify Minikube status: `minikube status`
- Check cluster resources: `kubectl get all`
