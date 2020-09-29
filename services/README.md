### Services

**Use CLI to create a ClusterIP**

```shell script
kubectl create service clusterip myservice --tcp:80:3000
```

**Use CLI to expose a pod**

```shell script
kubectl expose pod mypod --name=myservice --port=80 --target-port=8080
```

**Use CLI to expose pod outside the cluster**

```shell script
kubectl expose pod mypod --name=myservice --type=NodePort --port=80 --target-port=80
```

**Create ClusterIP using YAML**

```yaml

```
