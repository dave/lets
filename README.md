# letsencrypt demo

### Build
```
go get -u github.com/dave/lets
cd /home/dave/gopath/src/github.com/dave/lets
docker build -t gcr.io/lets-144108/lets-image .
gcloud docker push gcr.io/lets-144108/lets-image
```

### Deploy
```
gcloud config set compute/zone us-central1-b
gcloud container clusters create lets-cluster --num-nodes=1
kubectl run lets --image=gcr.io/lets-144108/lets-image:1.0 --port=443
kubectl expose deployment lets --type="LoadBalancer"
kubectl get service lets
```

### Delete
```
kubectl delete service lets
kubectl delete deployment lets
```

### Clean up
```
gcloud container clusters delete lets-cluster
```
