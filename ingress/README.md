## Types of Routing-Based Ingresses in Kubernetes ##
Basic Routing
Path-Based Routing
Host-Based Routing
Wildcard Routing

## Deploy APP
```
$ kubectl create namespace ingress-testing
$ kubectl create deploy webapp1 --image=nginx -n ingress-testing --dry-run=client -o yaml
$ kubectl create deploy webapp2 --image=nginx -n ingress-testing --dry-run=client -o yaml

$ kubectl create service clusterip webapp1 --tcp=80 -n ingress-testing --dry-run=client -o yaml
$ kubectl create service clusterip webapp2 --tcp=80 -n ingress-testing --dry-run=client -o yaml

$ kubectl -n ingress-testing apply -f webapp1-deployment.yml
$ kubectl -n ingress-testing apply -f webapp2-deployment.yml

$ kubectl get po,svc -n ingress-testing
```

## Basic Routing
$ kubectl create ingress basic-routing --rule="webapp1.example.local/*=webapp1-svc:80" -n ingress-testing --dry-run=client -o yaml
