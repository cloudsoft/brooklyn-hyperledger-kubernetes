# Kubernetes Hyperledger

This repository contains [Cloudsoft AMP](http://cloudsoft.io/getamp/) blueprints for a
[Hyperledger Fabric](https://github.com/hyperledger/fabric) v0.6.1 cluster deployment onto
[Kubernetes](https://kubernetes.io/).

## Deployment Instructions

### Step 1: Install Cloudsoft AMP

Use [this guide](http://docs.cloudsoft.io/tutorials/tutorial-get-amp-running.html) to install
AMP on your OS using the "DIY" option (downloading a `tar.gz` archive).

### Step 2: Deploy a Kubernetes Cluster

**NOTE**: You can skip this step if you already have a Kubernetes cluster running.

#### 2.1 Create a Deployment Location

In order to deploy a Kubernetes cluster with AMP, you must first configure a location to which
AMP will deploy it.

Use [this guide](http://docs.cloudsoft.io/locations/index.html) to learn more about AMP locations
and how to create your own.

**NOTE**: Your location must support CentOS 7.

#### 2.2 Deploy a Kubernetes Cluster to Your Location

Cloudsoft AMP comes bundled with the Cloudsoft Container Service (CCS) which supports the deployment
of Kubernetes clusters.

Use [this guide](http://docs.cloudsoft.io/ccs/tutorials/kubernetes-cluster.html) to deploy your own
Kubernetes Cluster using AMP and CCS.

**NOTE**: `kubernetes.initial.size` must be set to 6 or larger.

### Step 3: Deploy Hyperledger Fabric onto Your Kubernetes

#### 3.1 Add Hyperledger Fabric to the AMP Catalog

Download the [latest release JAR](https://github.com/cloudsoft/brooklyn-hyperledger-kubernetes/releases/download/0.16.0/hyperledger-kubernetes-0.16.0.jar)
from this repository and place it in the `deploy` directory inside the expanded AMP directory.

Then from the AMP UI home screen, perform the following steps:

* Click the square button in the top right corner
* Click "Blueprint importer"
* Copy and paste the [Hyperledger catalog file](hyperledger.bom) into the editor
* Click "Import" (button in bottom right corner)

#### 3.2 Deploy Hyperledger Fabric

From the AMP UI home screen, perform the following steps:

* Click "Blueprint composer" (tile in top row, second from the right)
* Click "YAML Editor" (button in top right corner)
* Copy and paste the [example YAML file](examples/hyperledger.yaml) into the editor
* Change the value of `endpoint` to the URL / port of your Kubernetes cluster
* Change the values of `identity` and `credential` if they differ from the example
* Click "Deploy" (button in bottom right corner)

**NOTE**: The example file contains the default `identity` and `credential` values for Kubernetes
clusters deployed with AMP.

In just a matter of moments you will have a Hyperledger Fabric cluster deployed onto your Kubernetes
cluster.
