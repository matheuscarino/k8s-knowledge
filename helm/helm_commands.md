# Helm

## Install Helm with Homebrew

$ brew install helm

## Helm version

$ helm version --short
v3.3.4+ga61ce56

## Helm add official Helm stable charts repo

$ helm repo add stable https://kubernetes-charts.storage.googleapis.com/

## List the charts you can install

$ helm search repo stable

## Make sure we get the latest list of charts

$ helm repo update

## Install a release of a chart with the stable/mysql [example]

$ helm install stable/mysql --generate-name

## List all Helm charts released

$ helm ls

## Uninstall a release

$ helm uninstall < release-name >

## Uninstall a release keeping the history

$ helm uninstall < release-name > --keep-history

## Get info aboult a release

$ helm status < release-name >

## Getting more info

$ helm get -h
