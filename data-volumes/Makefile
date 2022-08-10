build_push:
	docker build -t 8cox/kube-data:2 .
	docker push 8cox/kube-data:2

deploy:
	kubectl apply -f=deployment.yml,service.yml

deploy_pv:
	kubectl apply -f=host-pv.yml,host-pvc.yml

deploy_cfm:
	kubectl apply -f=configmap.yml

deploy_all:
	kubectl apply -f=deployment.yml,service.yml,host-pv.yml,host-pvc.yml,configmap.yml

clean:
	kubectl delete -f=deployment.yml,service.yml,host-pv.yml,host-pvc.yml,configmap.yml
