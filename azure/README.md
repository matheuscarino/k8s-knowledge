### Install CLI for Microsoft Azure
```
$ curl -L https://aka.ms/InstallAzureCli | bash
```
### Restart your shell
```
$ exec -l $SHELL
```
### Check AzureCLI version
```
$ az --version
```
##### [optional] If you don't have `kubectl` installed
```
$ az aks install-cli
```
### Initiate and log in
```
$ az login
```
### Create a resource group
```
$ az group create --name k8stesting --location eastus
```
### Create a Azure Active Directory for automation authentication and keep <appId> and <password>, we'll use next.
```
$ az ad sp create-for-rbac --skip-assignment
```
### Create a Kubernetes cluster, replace <appId> and <password> from the output of the last command
```
$ az aks create --resource-group k8stesting --name AKSTesting --kubernetes-version 1.17.3 --node-vm-size Standard_B2S --node-count 3 --service-principal <appId> --client-secret <password> --generate-ssh-keys
```
### Get your credentials and configure `kubectl` to manage your cluster
```
$ az aks get-credentials --resource-group k8stesting --name AKSTesting
```
### Check all nodes in your cluster
```
$ kubectl get nodes
```
### Delete your cluster
```
$ az aks delete --resource-group k8stesting --name AKSTesting
```