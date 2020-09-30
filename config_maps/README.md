### Config maps

**Use CLI to create config map from file***

```shell script
kubectl create configmap mycm --from=file=items.txt
```

**Use CLI to create config map from literals**

```shell script
kubectl create configmap mycm --from-literal=HOST=mongo --from-literal=PORT=27017
```

**Create config map using YAML**

_configmap.yaml_

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: mycm
data:
  HOST: "mongo"
  PORT: "27017"
```

**Mount config map as volume on pod**

_configmap_as_volume.yaml_

```yaml
...
spec:
  containers:
    - name: nginx
      image: nginx
      volumeMounts:
        - mountPath: /mnt/config
          name: myvolume
  volumes:
    - name: myvolume
      configMap:
        name: mycm
```

**Access configmap item as environment variable in pod**

_configmap_as_env_var.yaml_

```yaml
...
spec:
  containers:
    - name: nginx
      image: nginx
      env:
        - name: HOST
          valueFrom:
            configMapKeyRef:
              key: HOST
              name: mycm
```

**Inject all config map items as environment variables into pod**

_all_configmap_items_as_env_vars.yaml_

```yaml
...
spec:
  containers:
    - name: nginx
      image: nginx
      envFrom:
        - configMapRef:
            name: mycm
```
