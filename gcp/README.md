##### [notes] I'am using Debian 10 (with WSL) for this demo.
### Install CLI for Google Cloud Platform - GCP
```
$ curl https://sdk.cloud.google.com | bash
```
### Initiate, log in and select your GCP project
```
$ gcloud init
```
### Check `gcloud` version
```
$ gcloud --version
Google Cloud SDK 291.0.0
bq 2.0.57
core 2020.05.01
gsutil 4.50
```
### Enable the Compute Engine APIs for the project selected
```
$ gcloud services enable compute.googleapis.com
```
### Set a default region for compute services
```
$ gcloud config set compute/zone us-central1-a
```
##### [optional] Create a simple VM instance to ensure your compute services are enabled.
```
$ gcloud compute instances create "testing" --zone "us-central1-a" --machine-type "f1-micro"
```
##### [optional] Delete the VM instance created for testing
```
$ gcloud compute instances delete "testing"
```
### Now, create the Kubernetes cluster
```
$ gcloud container clusters create k8s-testing-1 \
--cluster-version latest --machine-type n1-standard-2 \
--image-type UBUNTU --disk-type pd-standard --disk-size 50 \
--no-enable-basic-auth --metadata disable-legacy-endpoints=true \
--scopes compute-rw,storage-ro,service-management,service-control,logging-write,monitoring \
--num-nodes "3" --enable-stackdriver-kubernetes \
--no-enable-ip-alias --enable-autoscaling --min-nodes 1 \
--max-nodes 5 --enable-network-policy \
--addons HorizontalPodAutoscaling,HttpLoadBalancing \
--enable-autoupgrade --enable-autorepair --maintenance-window "06:00"
```
### Download the credentials to access your K8s cluster
```
$ gcloud container clusters get-credentials k8s-testing-1
```
### Check the connection listing all nodes of cluster
```
$ kubectl get nodes
```
### Delete the k8s cluster.
```
$ gcloud container clusters delete k8s-testing-1
```

## Applications Docs

### Login on Google Cloud Registry

$ gcloud auth configure-docker

### Deploying a simple golang web app

$ cd simple-golang-webapp/
$ docker build -t gcr.io/<gcp-project-id>/hello-app:v1 .
$ docker push gcr.io/<gcp-project-id>/hello-app:v1
$ kubectl create deployment hello-app --image=gcr.io/<gcp-project-id>/hello-app:v1
$ kubectl scale deployment hello-app --replicas=3
$ kubectl autoscale deployment hello-app --cpu-percent=80 --min=1 --max=5
$ kubectl expose deployment hello-app --name=hello-app-service --type=LoadBalancer --port 80 --target-port 8080

### Delete it

$ kubectl delete service hello-app-service
$ kubectl delete deployment hello-app
$ gcloud container images delete gcr.io/carinotecnologia/hello-app:v1  --force-delete-tags --quiet
