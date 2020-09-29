### Replica sets

**Create replica set**
```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: myrs
spec:
  replicas: 2
  selector:
    matchLabels:
      app: backend
  template:
    metadata:
      labels:
        app: backend
    spec:
      containers:
        - name: nginx
          image: nginx
```

**Use CLI to scale replica set**
```shell script
kubectl scale replicaset myrs --replicas=3
```
