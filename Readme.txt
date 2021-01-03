Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))

choco install minikube

REM Used linux
minikube start
minikube kubectl -- get pods -A
minikube dashboard

# DID NOT work
minikube start --vm-driver hyperv --hyperv-virtual-switch "ExternalSwitch"


kubectl get services
minikube addons list

kubectl get nodes
minikube status
kubectl version
kubectl create deployment nginx-depl --image=nginx
kubectl get deployment
kubectl get deployment nginx-deployment -o yaml
kubectl get pod
kubectl get pod -o wide
kubectl get replicaset
kubectl edit deployment nginx-depl

# nginx
kubectl logs nginx-depl-7fc44fc5d4-krskg

kubectl create deployment mongo-depl --image=mongo

#mongo
kubectl describe pod mongo-depl-5fd6b7d4b4-2wbwm
kubectl logs mongo-depl-5fd6b7d4b4-2wbwm

debugging
kubectl exec -it mongo-depl-5fd6b7d4b4-2wbwm -- bin/bash

kubectl get deployment
kubectl delete deployment mongo-depl


# create nginx-deployment.yml file
# copy file from https://kubernetes.io/docs/concepts/workloads/controllers/deployment/
kubectl apply -f nginx-deployment.yaml

# define and run service
kubectl apply -f nginx-deployment.yaml
kubectl apply -f nginx-service.yaml

kubectl get service
kubectl describe service nginx-service


kubectl delete deployment nginx-deployment
kubectl delete service nginx-service
kubectl delete -f nginx-deployment.yaml
kubectl delete -f nginx-service.yaml


kubectl get deployment nginx-deployment -o yaml > nginx-deployment-result.yaml


# namespaces
kubectl get namespace
kubectl cluster-info
kubectl create namespace my-namespace

kubectl api-resources --namespaced=false

# installing kubens for linux
choco install kubectx
# for windows
https://github.com/thomasliddledba/kubenswin/releases/tag/0.1.1
https://developers.redhat.com/blog/2019/05/27/command-line-tools-for-kubernetes-kubectl-stern-kubectx-kubens/

kubenswin set my-namespace
kubenswin ls
kubenswin set default
kubenswin ls
