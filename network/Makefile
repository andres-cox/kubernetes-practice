build_push:
	docker build -t 8cox/kube-users ./users-api/
	docker build -t 8cox/kube-auth ./auth-api/
	docker build -t 8cox/kube-tasks ./tasks-api/
	docker build -t 8cox/kube-frontend ./frontend/
	docker push 8cox/kube-users
	docker push 8cox/kube-auth
	docker push 8cox/kube-tasks
	docker push 8cox/kube-frontend

deploy:
	kubectl apply -f=\
	kubernetes/users-deployment.yml,\
	kubernetes/users-service.yml,\
	kubernetes/auth-deployment.yml,\
	kubernetes/auth-service.yml,\
	kubernetes/tasks-deployment.yml,\
	kubernetes/tasks-service.yml,\
	kubernetes/frontend-deployment.yml,\
	kubernetes/frontend-service.yml

clean:
	kubectl delete -f=\
	kubernetes/users-deployment.yml,\
	kubernetes/users-service.yml,\
	kubernetes/auth-deployment.yml,\
	kubernetes/auth-service.yml,\
	kubernetes/tasks-deployment.yml,\
	kubernetes/tasks-service.yml,\
	kubernetes/frontend-deployment.yml,\
	kubernetes/frontend-service.yml

expose_users:
	minikube service users-service

expose_tasks:
	minikube service tasks-service

expose_frontend:
	minikube service frontend-service

# note in order to frontend work need to have some tasks posted otherwise won`t show up
# expose all services at once
expose_all:
	minikube service list