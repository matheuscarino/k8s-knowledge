## Useful minikube commands

```
# Install minikube on Windows 10 Pro
$ choco install minikube

# Start a k8s cluster locally with default settings.
$ minikube start

# Check status of k8s cluster created.
$ minikube status

# Open k8s dashboard
$ minikube dashboard

# Configure networking routes to every service of type: LoadBalancer
$ minikube tunnel

# Delete a k8s cluster.
$ minikube delete
```