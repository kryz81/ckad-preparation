### Nodes

**Add label to node**

```shell script
kubectl label node app=frontend
```

**Show the list of nodes with labels**

```shell script
kubectl get node --show-labels
```

**Create pod on specific node using node selector**

```shell script
...
spec:
  nodeSelector:
    app: backend
  containers:
    - name: nginx
      image: nginx
```

**Create pod on specific node using node name**

```shell script
...
spec:
  nodeName: docker-desktop
  containers:
    - name: nginx
      image: nginx
```
