Sevice k8s: Điều phối traffic vào đúng các pod
- cluster ip (premise) - main
- NodePort
- loadbalancer (for cloud) - main
- externalname
```
NodePort / ClusterIP: rancher.nnson128.tech
	- create service type: NodePort / ClusterIP
		+ tab selector: label in yaml
	- done
	
```
