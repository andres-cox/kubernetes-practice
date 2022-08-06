build:
	docker build -t 8cox/kube-first-app .

push:
	docker push 8cox/kube-first-app .

update:
	docker build -t 8cox/kube-first-app:2 .
	docker push 8cox/kube-first-app:2

deploy:
	kubectl create deployment first-app --image=8cox/kube-first-app

dashboard:
	minikube dashboard

expose:
	kubectl expose deployment first-app --type=LoadBalancer --port=8080

services:
	kubectl get services

minikube_service:
	minikube service first-app

scale:
	kubectl scale deployment/first-app --replicas=3

update_deployment: 
	kubectl set image deployment/first-app kube-first-app=8cox/kube-first-app:2 

# force ErrImagePull 
break:
	kubectl set image deployment/first-app kube-first-app=8cox/kube-first-app:3 

rollout:
	kubectl rollout status deployment/first-app
	
undo:
	kubectl rollout undo deployment/first-app

history:
	kubectl rollout history deployment/first-app

describe_history:
	kubectl rollout history deployment/first-app --revision=3

undo_revision:
	kubectl rollout undo deployment/first-app --to-revision=1

clean:
	kubectl delete service first-app
	kubectl delete deployment first-app

apply_deployment:
	kubectl apply -f=deployment.yml

apply_service:
	kubectl apply -f=service.yml

clean_deployments:
	kubectl delete -f=deployment.yml,service.yml

apply_master_deployment:
	kubectl apply -f=master-deployment.yml

clean_master:
	kubectl delete -f=master-deployment.yml

expose_minikube_service:
	minikube service backend
