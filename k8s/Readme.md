# Building the application and pushing to docker hub
## cd webapp

``` bash
docker build -t flaskapp .

docker login --username=monihub
docker tag flaskapp monihub/flaskapp

docker push monihub/flaskapp
```

# Deploying the application to kubernetes
## cd k8s

``` bash
kubectl apply ‑f nginx‑configmap.yaml
kubectl apply ‑f redis‑deployment.yaml
kubectl apply ‑f webapp‑deployment.yaml
kubectl apply ‑f nginx‑deployment.yaml
```