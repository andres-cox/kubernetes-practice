install_helm:
	curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
	chmod 700 get_helm.sh
	./get_helm.sh

add_jenkins_repo:
	helm repo add jenkins https://charts.jenkins.io

update_repos:
	helm repo update

list_repos:
	helm repo list

# https://artifacthub.io/packages/helm/jenkinsci/jenkins
# can also work without minikube service check notes when installing
jenkins_install:
	helm install demo-jenkins jenkins/jenkins

jenkins_minikube_install:
	helm install demo-jenkins jenkins/jenkins -f jenkins-values.yml

# use URL exposed with "/login"
expose_minikube_service:
	minikube service demo-jenkins

# TO check resources deployed
jenkins_manifest:
	helm get manifest demo-jenkins

# to check values.yaml of chart that can be overwrited
show_values:
	helm show values jenkins/jenkins

# pull helm package
pull_chart:
	helm pull jenkins/jenkins

# might need to modify for latest version
unzip_package:
	tar zxvf jenkins-4.1.17.tgz

