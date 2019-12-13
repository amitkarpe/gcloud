check:
	kubectl get all

list:
	@echo kubectl create -f  redis-master-deployment.yaml
	@echo kubectl create -f     redis-master-service.yaml
	@echo kubectl create -f     redis-slave-deployment.yaml
	@echo kubectl create -f     redis-slave-service.yaml
	@echo kubectl create -f     frontend-deployment.yaml
	@echo kubectl create -f     frontend-service.yaml

ns:
	@echo create new namespace and do all operation within that namespace
	kubectl create ns gb
	kubectl config set-context --current --namespace=gb
	kubectl config view --minify | grep namespace:

deploy:
	kubectl create -f  redis-master-deployment.yaml
	kubectl create -f     redis-master-service.yaml
	kubectl create -f     redis-slave-deployment.yaml
	kubectl create -f     redis-slave-service.yaml
	kubectl create -f     frontend-deployment.yaml
	kubectl create -f     frontend-service.yaml
	kubectl get pod -w

service:
	kubectl get svc

lb:
	kubectl delete -f  frontend-service.yaml | echo "Confirmed that frontend service is not exist."
	cp  frontend-service.yaml lb-frontend-service.yaml
	sed -i -e     's/NodePort/LoadBalancer/g' lb-frontend-service.yaml
	kubectl create -f  lb-frontend-service.yaml
	kubectl get svc frontend -w

