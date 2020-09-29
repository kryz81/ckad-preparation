### Pods

**Use CLI to run pod with labels**
```shell script
kubectl run mypod --image=nginx --restart=Never --labels=app=backend
```

**Get pod list with labels**
```shell script
kubectl get po --show-labels
```

**Get pods with specific label**
```shell script
kubectl get po -l app=backend
```

**Use CLI to add label to a pod**
```shell script
kubectl label pod mypod mode=production
````

**Use CLI to change the value of existing pod label**
```shell script
kubectl label pod mypod app=frontend --overwrite
``` 

**Use CLI to remove label from pod**
```shell script
kubectl label pod mypod app-
```
