# Reading and practicing Kubernetes

## Create a Kubernetes cluster on major cloud providers

### Azure instructions
```
./azure
```
### Google Cloud Plataform instructions
```
./gcp
```
### AWS instructions
```
./aws
```

## Useful commands

### For debugging

```
## Applying a Deployment
# kubectl apply -f <deployment-filename>.yaml

## Verifying a Deployment
# kubectl rollout status deployment <deployment-name>

## List all Deployments
# kubectl get deployments

## List all ReplicaSets and Pods #tip
# kubectl get rs,pods

## Edit a Deployment
# kubectl edit deployments <deployment-name>

## Create a annotation for a change
# kubectl annotate deployment <deployment-name> kubernetes.io/change-cause="<annotation-message>"

## Describe Deployments
# kubectl get deployments

## See the deployment history
# kubectl rollout history deployment <deployment-name>

## Roll back the last rollout
# kubectl rollout undo deployment <deployment-name>

## Roll back to a specific revision number
# kubectl rollout undo deployment <deployment-name> --to-revision=1

## Remove a Deployment
$ kubectl delete deployment <deployment-name>

## Viewing Pod Logs
# kubectl logs <pod-name>

## Interactive shell (Bash) inside the running container
$ kubectl exec -it <pod-name> -- bash

## Copying file to and from a container
$ kubectl cp <pod-name>:/path/remote/file /path/to/destination/
or
$ kubectl cp /path/local/file <pod-name>:/path/remote/file

## Check used ports by a Pod
kubectl get pod <pod-name> --template='{{(index (index .spec.containers 0).ports 0).containerPort}}{{"\n"}}'

## Port Forward
$ kubectl port-forward <pod-name> <local-port>:<container-port>
or
$ kubectl port-forward pods/<pod-name> <local-port>:<container-port>
or
$ kubectl port-forward deployment/<pod-name> <local-port>:<container-port>
or
$ kubectl port-forward replicaset/<pod-name> <local-port>:<container-port>
or
$ kubectl port-forward service/<pod-name> <local-port>:<container-port>
```
## Ingress Controllers

### Contour './contour/'
Project: https://github.com/projectcontour/contour


## Keeping notes
> ***Liveness*** determines if an application is running properly.

> ***Readiness*** describes when a container is ready to serve user requests.


# References:

## Books

[Kubernetes – Up and Running, Dive Into the Future of Infrastructure by Brendan Burns, Joe Beda, Kelsey Hightower][1]
[Kubernetes – A Complete DevOps Cookbook: Build and manage your applications, orchestrate containers, and deploy cloud-native services][2]
[Kubernetes Best Practices - Blueprints for Building Successful Applications on Kubernetes][3]
[Kubernetes Operators - Automating the Container Orchestration Platform][4]
[Container Security - Fundamental Technology Concepts that Protect Containerized Applications][5]

## Kubernetes Documentation

### Port Forward
https://kubernetes.io/docs/tasks/access-application-cluster/port-forward-access-application-cluster/

### Ingress Controllers
https://kubernetes.io/docs/concepts/services-networking/ingress-controllers/

## Helm
https://helm.sh/docs/intro/

[1]: https://www.oreilly.com/library/view/kubernetes-up-and/9781492046523/
[2]: https://www.packtpub.com/product/kubernetes-a-complete-devops-cookbook/9781838828042
[3]: https://www.oreilly.com/library/view/kubernetes-best-practices/9781492056461/
[4]: https://www.oreilly.com/library/view/kubernetes-operators/9781492048039/
[5]: https://www.oreilly.com/library/view/container-security/9781492056690/
