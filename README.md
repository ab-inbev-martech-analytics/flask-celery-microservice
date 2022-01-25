# flask-celery-microservice

```
sudo apt update -y
sudo apt upgrade -y
sudo apt install -y curl wget apt-transport-https
wget https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo cp minikube-linux-amd64 /usr/local/bin/minikube
sudo chmod +x /usr/local/bin/minikube
curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
kubectl version -o yaml
```

```bash
minikube start
kubectl apply -f postgres.yaml
kubectl apply -f rabbitmq.yaml
kubectl apply -f flask_server.yaml
kubectl apply -f celery_workers.yaml
kubectl port-forward --namespace flask-backend service/flask-server 8000:80
curl -X POST http://localhost:8000/report
curl http://localhost:8000/report/b40454cc-9054-46ab-9740-396516cc0d0b
```
