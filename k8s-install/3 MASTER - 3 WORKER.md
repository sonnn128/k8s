```
# k8s-master-1
sudo kubeadm init --control-plane-endpoint "192.168.1.111:6443" --upload-certs 
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config

# k8s-master-2 / k8s-master-3
kubeadm join 192.168.1.111:6443 --token 57xvrz.fmpg8cuyp0k2mbrz \
      --discovery-token-ca-cert-hash sha256:cfeaba52ba959af7ef89cec6db9a07a5a1c93dcb004250556e3841348dc01aec \
      --control-plane --certificate-key 9a49d865bd854dea545b9222b20d9719296853cf65846f9ce22b1378e30a4b42

# K8S-MASTER-1
kubectl taint nodes k8s-master-1 node-role.kubernetes.io/control-plane:NoSchedule- 
kubectl taint nodes k8s-master-2 node-role.kubernetes.io/control-plane:NoSchedule- 
kubectl taint nodes k8s-master-3 node-role.kubernetes.io/control-plane:NoSchedule- 
```
