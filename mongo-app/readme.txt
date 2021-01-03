# create mongo deployment
# check how user name and password is saved in config map and secret

powershell "[convert]::ToBase64String([Text.Encoding]::UTF8.GetBytes(\"username\"))"
powershell "[convert]::ToBase64String([Text.Encoding]::UTF8.GetBytes(\"password\"))"

cd F:\learn\kubernetes\mongo-app
kubectl apply -f mongodb-secret.yaml
kubectl get secret


kubectl apply -f mongo-deployment.yaml

kubectl get pod

kubectl apply -f mongo-deployment.yaml
kubectl get service
kubectl describe service mongodb-service

kubectl get all | grep mongodb


# install mongo express
kubectl apply -f mongodb-configmap.yaml
kubectl apply -f mongoexp-deployment.yaml


kubectl delete -f mongoexp-deployment.yaml
kubectl delete -f mongo-deployment.yaml

kubectl delete -f mongodb-secret.yaml
kubectl delete -f mongodb-configmap.yaml


kubectl get configmap -o wide
kubectl get configmap -n my-namespace
kubectl get configmap -o yaml
kubectl describe mongodb-configmap
