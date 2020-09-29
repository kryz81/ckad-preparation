### Logging

**Use CLI to show logs of a specific pod container**
```shell script
kubectl logs mypod -c nginx
```

**Use CLI to show logs of all containers**
```shell script
kubectl logs mypod --all-containers
```

**Use CLI to show logs of previous (crashed) container instance**
```shell script
kubectl logs mypod -c nginx --previous
```
