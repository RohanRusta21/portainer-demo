# portainer-demo

### Verify your storage-class , as portainer uses persistent volume to make it state persistence throughout the lifecycle.
```shell
kubectl get sc
kubectl patch storageclass <storage-class-name> -p '{"metadata": {"annotations":{"storageclass.kubernetes.io/is-default-class":"true"}}}'
```

### Install using kubectl YAML manifests
```shell
kubectl apply -n portainer -f https://downloads.portainer.io/ce2-19/portainer.yaml**
```

### Install using Helm (Storage class steps has to be followed here too)
```shell
helm repo add portainer https://portainer.github.io/k8s/
helm repo update
helm upgrade --install --create-namespace -n portainer portainer portainer/portainer --set tls.force=true
```
