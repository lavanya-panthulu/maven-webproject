minikube start --driver=docker
kubectl create deployment myapp --image=nginx
 kubectl get pods
 kubectl expose deployment myapp --type=NodePort --port=80
 minikube service myapp --url
