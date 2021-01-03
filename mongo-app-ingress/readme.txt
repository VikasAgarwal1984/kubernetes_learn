# for older steps see mogo-app readme.txt

#ingress setup starts here
# start docker eng in hyperv mode, wsl2 did not work for me.
minikube addons enable ingress

minikube delete
minikube addons enable ingress
# install minikube 1.16.0 version using choco
choco install minikube --version 1.16.0
minikube start --vm-driver hyperv --hyperv-virtual-switch "ExternalSwitch"
minikube start


kubectl get pod -n kube-system
# will see one of the o/p
# ingress-nginx-controller-558664778f-x87d7   1/1     Running     0          7m39s

kubectl get ns
kubectl get services -n kube-system
kubectl get services -n kubernetes-dashboard
kubectl get all -n kubernetes-dashboard

kubectl apply -f dashboard-ingress.yaml
kubectl get ingress -n kubernetes-dashboard


