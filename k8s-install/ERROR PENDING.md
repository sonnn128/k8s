```
kubectl get pods -n kube-system | grep calico
IF NOT LET'S INSTALL CALICO
kubectl apply -f https://raw.githubusercontent.com/projectcalico/calico/v3.25.0/manifests/calico.yaml

kubectl -n kube-system edit configmap coredns
hosts {
  192.168.1.114 rancher.nnson128.vn
  fallthrough
}
kubectl -n kube-system rollout restart deployment coredns
WAIT 2 MINUTES
kubectl run -it --rm --restart=Never busybox --image=busybox -- nslookup rancher.nnson128.vn

kubectl apply -f ....
```
