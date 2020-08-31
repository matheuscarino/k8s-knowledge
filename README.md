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

## Kubernetes Documentation

### Port Forward
https://kubernetes.io/docs/tasks/access-application-cluster/port-forward-access-application-cluster/

[1]: https://www.oreilly.com/library/view/kubernetes-up-and/9781492046523/