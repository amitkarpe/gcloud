# Example: Guestbook application on Kubernetes

This directory contains the source code and Kubernetes manifests for PHP
Guestbook application.

Follow the tutorial at https://kubernetes.io/docs/tutorials/stateless-application/guestbook/.

Review Makefile
Run following command in sequnce

create new namespace and do all operation within that namespace

```
kubectl create ns gb
kubectl config set-context --current --namespace=gb
kubectl config view --minify | grep namespace:
```

And run following command to check any existing objects in "gb" namespaces, list all command and deploy guestbook and create load balancer (if on cloud).

```
make # To list all objects
make list
make deploy
make 
```

- If need to test load balancer then run ( If you are running it on cloud, then new load balancer will be get created. And EXTERNAL-IP will be available to access Guest Book service.
```
make lb 
make

```

