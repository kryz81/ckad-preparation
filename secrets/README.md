### Secrets

**Encode text**

```shell script
echo -n "12345" | base64
```

**Use CLI to create secret from file**

```shell script
kubectl create secret genetic mysecret --from-file=secrets.txt
```

**Use CLI to create secret from literals**

```shell script
kubectl create secret generic mysecret --from-literal=user=myuser
```

**Mount secret as volume on pod**

_secret_as_volume.yaml_

```yaml
...
spec:
  containers:
    - name: nginx
      image: nginx
      volumeMounts: # mount volume
        - mountPath: /mnt
          name: mysecret
  volumes:
    - name: mysecret # create volume from secret
      secret:
        secretName: mysecret
```

**Access secret item as environment variable in pod**

_secret_as_env_var.yaml_

```yaml
...
spec:
  containers:
    - name: nginx
      image: nginx
      env:
        - name: USER
          valueFrom:
            secretKeyRef: # get value of "user" key, look in "mysecret" secret
              name: mysecret
              key: user
```

**Inject all secret items as environment variables into pod**

_all_secret_items_as_env_vars.yaml_

```yaml
...
spec:
  containers:
    - name: nginx
      image: nginx
      envFrom:
        - secretRef:
            name: mysecret
```
