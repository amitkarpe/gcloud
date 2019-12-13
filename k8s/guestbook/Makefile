check:
	kubectl get all

list:
	@echo kubectl create -f  redis-master-deployment.yaml
	@echo kubectl create -f     redis-master-service.yaml
	@echo kubectl create -f     redis-slave-deployment.yaml
	@echo kubectl create -f     redis-slave-service.yaml
	@echo kubectl create -f     frontend-deployment.yaml
	@echo kubectl create -f     frontend-service.yaml


deploy:
	kubectl create -f  redis-master-deployment.yaml
	kubectl create -f     redis-master-service.yaml
	kubectl create -f     redis-slave-deployment.yaml
	kubectl create -f     redis-slave-service.yaml
	kubectl create -f     frontend-deployment.yaml
	kubectl create -f     frontend-service.yaml

service:
	kubectl get svc

lb:
	kubectl delete -f  frontend-service.yaml
	sed -i -e     's/NodePort/LoadBalancer/g'     frontend-service.yaml
	kubectl create -f  frontend-service.yaml
	kubectl get svc frontend -w

