### Rolling updates

**Use CLI to set new image on deployment container**

```shell script
kubectl set image deployment mydeployment mycontainer=nginx:1.18.0
```

**Use CLI to check status of deployment rollout**

```shell script
kubectl rollout status deployment mydeployment
```

**Use CLI to check deployment rollout history**

```shell script
kubectl rollout history deployment mydeployment
```

**Use CLI to roll back to the previous version**

```shell script
kubectl rollout undo deployment mydeployment
```

**Use CLI to roll back to specific revision**

```shell script
kubectl rollout undo deployment mydeployment --to-revision=2
```
