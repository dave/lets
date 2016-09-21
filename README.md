# lets
letsencrypt demo

### setup
```
go get -u github.com/davelondon/lets
cd /home/dave/gopath/src/github.com/davelondon/lets
docker build -t gcr.io/lets-144108/lets-image .
gcloud docker push gcr.io/lets-144108/lets-image
```

```
gcloud config set compute/zone us-central1-b
gcloud container clusters create lets-cluster --num-nodes=1
kubectl run lets --image=gcr.io/lets-144108/lets-image:1.0 --port=80 --port=443
```


