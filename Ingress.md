a ingress must have [ingress controller](https://kubernetes.io/docs/concepts/services-networking/ingress/)

recommend ingress controller:
- nginx ingress controller
- HAProxy ingress
- Kong ingress controller


install nginx ingress controller with helm

# install helm
search "helm releases"
wget linux amd64
tar xvf helm.tar
root@k8s-master-1:~# mv linux-amd64/helm /usr/bin
root@k8s-master-1:~# helm version

# install ingress nginx (https://github.com/kubernetes/ingress-nginx)
helm repo add ingress-nginx http://kubernetes.github.io/ingress-nginx/
helm repo update
helm search repo nginx
helm pull ingress-nginx/ingress-nginx 
tar -xzf ingress-nginx-4.12.3.tgz
vi ingress-nginx/values.yaml
	service.type = NodePort
	service.nodePorts: 
		http: "30080"
		https: "30443"

cp -rf ingress-nginx /home/devops
su - devops
helm -n <namespace> install <release name> -f ingress-nginx/values.yml <helm chart>
kubectl create namespace ingress-nginx
helm -n ingress-nginx install ingress-nginx -f ingress-nginx/values.yaml ingress-nginx
