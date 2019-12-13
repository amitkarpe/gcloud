# Source: https://cloud.google.com/kubernetes-engine/docs/quickstart
# Idea to demonstrate GKE

check:
	kubectl get all

ns:
	@echo create new namespace and do all operation within that namespace
	kubectl create ns hello
	kubectl config set-context --current --namespace=gb
	kubectl config view --minify | grep namespace:


deploy1:
	kubectl create deployment hello-server --image=gcr.io/google-samples/hello-app:1.0
	kubectl expose deployment hello-server --type LoadBalancer --port 80 --target-port 8080
	kubectl get service hello-server -w
	kubectl get pods


deploy2:
	kubectl delete deployment,svc hello-server
	kubectl create deployment hello-server --image=gcr.io/google-samples/hello-app:2.0
	kubectl expose deployment hello-server --type LoadBalancer --port 80 --target-port 8080
	kubectl get service hello-server -w
	kubectl get pods
