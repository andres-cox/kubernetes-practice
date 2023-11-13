# Install linkerd following https://linkerd.io/2.14/getting-started/

start_minikube:
	minikube start

install_linkerd_fish:
	curl --proto '=https' --tlsv1.2 -sSfL https://run.linkerd.io/install | sh
	fish_add_path /home/andres/.linkerd2/bin
	linkerd version
	linkerd check --pre
	linkerd install --crds | kubectl apply -f -
	linkerd install --set proxyInit.runAsRoot=true | kubectl apply -f - 

validate_linkerd:
	linkerd check

deploy_app:
	kubectl apply -f emojivoto.yml

# wait pods before running port forward
serve_web:
	kubectl -n emojivoto port-forward svc/web-svc 8080:80

apply_linkerd_in_clusrer:
	kubectl get -n emojivoto deploy -o yaml | linkerd inject - | kubectl apply -f -
	linkerd -n emojivoto check --proxy
	linkerd viz install | kubectl apply -f - 
	linkerd viz dashboard &

destroy_cluster:
	kubectl delete -f emojivoto.yml
	minikube stop