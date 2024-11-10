# kubectl
```
# Create Namespace, Deployment, Service และ Ingress
$ kubectl create ns my-web --dry-run=client -o yaml
$ kubectl create deployment myweb --image=nginx -n my-web --dry-run=client -o yaml
$ kubectl create service clusterip myweb --tcp=80:80 -n my-web --dry-run=client -o yaml 
$ kubectl create ingress myweb --rule="myweb.home.lan/*=myweb:80" -n my-web --dry-run=client -o yaml 

# ConfigMap and Secret
$ kubectl create configmap myweb-configmap --from-file=./config/config.html --from-file=config1.html=./config/config.txt -n my-web --dry-run=client -o yaml
$ kubectl create secret generic myweb-secret --from-literal=username=oom --from-literal=password=123456 -n my-web --dry-run=client -o yaml

# Encode base64
$ echo -n "123456" | base64
$ echo "MTIzNDU2" | base64 -d
$ kubectl get pod -n myweb
$ kubectl exec -it <pod name> -n my-web -- /bin/bash
$ ls /usr/share/nginx/secret

# Delete All Namespace
$ kubectl delete ns my-web
```