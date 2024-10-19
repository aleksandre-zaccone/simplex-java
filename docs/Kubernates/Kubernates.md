# Kubernetes

## Kubernetes CLI

check version - kubectl version --client
check version with all detail - kubectl version --client --output=yaml

By default, kubectl configuration is located at ~/.kube/config.

Start minicube cluster - minikube start

see process list - kubectl get po -A

## Minikybe
create Minikube cluster - kubectl -n kubernetes-dashboard create token admin-user

run Dashboard - Start a new terminal, and leave this running.
minikube dashboard

create a new deployment - kubectl create deployment
view deployments - kubectl get deployments
view pods - kubectl get pods
view cluster events - kubectl get events
view crl configurations - kubectl config view
view logs for containers /pods - kubectl logs hello-node-5f76cf6ccf-br9b5

Pods that are running inside Kubernetes are running on a private, isolated network. By default they are visible from other pods and services within the same Kubernetes cluster, but not outside that network.
he kubectl proxy command can create a proxy that will forward communications into the cluster-wide, private network. The proxy can be terminated by pressing control-C and won't show any output while it's running.


View the Service you created:- kubectl get services
opens up a browser window that serves your app and shows the app's response -minikube service hello-node


minicubwe addones - minikube addons list
inable addons - minikube addons enable metrics-server

delete
kubectl delete service hello-node
kubectl delete deployment hello-node

minikube stop

 - 


## Kubernetes Dashboard

to login run proxy from /home/aablotia/Kubernetes/

kubectl proxy         

generate token - kubectl -n kubernetes-dashboard create token admin-user