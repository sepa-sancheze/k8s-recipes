# Kubernetes recipes

Hello!

In this repo you will find important information and tutorials about Kubernetes.

At the begining we will be using minikube to run our cluster locally, and then we will deploy Instances so we can see a k8s cluster in action.

## Using Minikube

First, we need to install `minikube` in our machine, to do it, we can go to [this link](https://minikube.sigs.k8s.io/docs/start/?arch=%2Fmacos%2Fx86-64%2Fstable%2Fbinary+download)

Once that `minikube` is installed, we can start the cluster with the following:

    minikube start

Once that we are done we can:

- Stop the cluster

        minikube stop

- Delete the cluster

        minikube delete


It is recommended that we use `kubectl` instead of `minikube kubectl`.