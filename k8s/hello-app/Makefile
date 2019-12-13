# Source: https://cloud.google.com/kubernetes-engine/docs/quickstart
# Idea to demonstrate GKE

ns=hello-app
ns:
	@echo create new namespace and do all operation within that namespace
	kubectl create ns ${ns}
	kubectl config set-context --current --namespace=${ns}
	kubectl config view --minify | grep namespace:

check:
	kubectl get all -n ${ns}



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

test:
	curl $$(kubectl get svc -o=custom-columns=IP:.status.loadBalancer.ingress[].ip --no-headers)
	
end:
	@echo Going to delete all objects created in "${ns}"" namespace.
	kubectl delete ns ${ns} --v=2
