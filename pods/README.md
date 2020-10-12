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

**Use port forwarding to connect to a pod**

```shell script
kubectl port-forward mypod 8080:80
```

**Force pod delete**

```shell script
kubectl delete pod mypod --force --grace-period=0
````

**Use CLI to create pod which uses bash image and runs a bash command**

```shell script
kubectl run mypod --image=bash --restart=Never -- bash -c "hostname && && date && sleep 1d"
````

**Create pod with resource limits**

```yaml
...
spec:
  containers:
    - name: nginx
      image: nginx
      resources:
        limits: # pod won't grow above these limits
          cpu: "1"
          memory: "10Mi"
        requests: # pod will get at least this amount
          cpu: "0.5"
          memory: "5Mi"
```

**Create pod with file directory, which survives pod crash/restart**

```yaml
...
spec:
  containers:
    - name: nginx
      image: nginx
      volumeMounts:
        - mountPath: /mnt
          name: myvolume
  volumes:
    - name: myvolume
      emptyDir: {}
```

**Create environment variable in pod with yaml definition field value**

```yaml
...
metadata:
  name: mypod
spec:
  containers:
    - name: nginx
      image: nginx
      env:
        - name: MYPODNAME
          valueFrom:
            fieldRef:
              fieldPath: metadata.name
```
