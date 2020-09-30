### Deployments

**Create deployment using CLI**

```shell script
kubectl create deployment mydeployment --image=nginx
```

**Create deployment using YAML**

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: mydeployment
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
          ports:
            - containerPort: 80
```

**Scale deployment**

```shell script
kubectl scale deployment mydeployment --replicas=4
```

**Pause deployment**

```shell script
kubectl rollout pause deployment mydeployment
```

**Resume deployment**

```shell script
kubectl rollout resume deployment mydeployment
```

