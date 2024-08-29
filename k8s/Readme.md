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

# Deploying the application to kubernetes(minikube and argoCD)
# Create a new application in argocd

``` bash
kubectl port-forward svc/argocd-server -n argocd 8081:443
```

## portforwarted to 8081 use the browser to access it using 8081
## login to argocd using the username and password and create a new application

### Application: FLASKDEMO

### Project
- **Name:** default

### Annotations
- **Cluster:** in-cluster (https://kubernetes.default.svc)
- **Namespace:** flaskdemo

### Created At
- **Date:** 08/29/2024
- **Time:** 11:41:06 (41 minutes ago)

### Repository Information
- **Repo URL:** [https://github.com/mohan2020coder/doc_kub.git](https://github.com/mohan2020coder/doc_kub.git)
- **Target Revision:** HEAD
- **Path:** k8s

### Sync Options
- **Option:** CreateNamespace

### Retry Options
- **Status:** Retry disabled

### Status
- **Sync:** Synced to HEAD (88c22fc)
- **Health:** Healthy


``` bash
kubectl get pods -n flaskdemo
minikube service list
minikube service nginx --url -n flaskdemo
```