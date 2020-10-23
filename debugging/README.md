### Debugging

**Get events from etcd**

```shell script
kubectl get events
```

**Check from pod if a service is running**

_from pod_

```shell script
curl myservice
# or
wget -O- myservice
# or
nslookup myservice
```

**Use CLI to run command on container**

```shell script
kubectl exec mypod sleep 10s
```
