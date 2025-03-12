docker build -t dattranabs/my-app:latest .
docker push dattranabs/my-app:latest
------

kubectl apply -f k8s/mongodb/
kubectl apply -f k8s/nodejs/
----
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
----
kubectl apply -f k8s/argocd-app.yaml -n argocd
----
kubectl get svc nodejs-service

--------------------
Bật Minikube với driver Docker:
minikube start --driver=docker

Kiểm tra Minikube đang chạy:
kubectl get nodes

Deploy MongoDB
kubectl apply -f k8s/mongodb/mongodb-deployment.yaml
kubectl apply -f k8s/mongodb/mongodb-service.yaml

Kiểm tra:
kubectl get pods -l app=mongodb

Deploy Node.js
kubectl apply -f k8s/nodejs/deployment.yaml
kubectl apply -f k8s/nodejs/service.yaml

Kiểm tra:
kubectl get pods -l app=my-app

Lấy danh sách Service
kubectl get svc

minikube service my-app

kubectl port-forward svc/argocd-server -n argocd 8080:443
