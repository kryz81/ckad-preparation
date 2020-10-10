### Persisted volumes

**Create simple persistent volume stored on Kubernetes node**

_persistentvolume.yaml_

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: mypv
spec:
  storageClassName: manual
  capacity:
    storage: "1Gi"
  accessModes:
    - ReadWriteOnce # only single node can mount this volume (in read-write mode)
  hostPath:
    path: /mnt/pv # files location
```

**Create claim**

_persistentvolumeclaim.yaml_

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: mypvc
spec:
  storageClassName: manual
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: "0.5Gi" # I need 0.5 GB, Kubernetes should find a persistent volume for it
```

**Mount volume in pod**

_pod_with_persistent_volume.yaml_

```yaml
...
spec:
  containers:
    - name: nginx
      image: nginx
      volumeMounts: # mount volume from claim
        - mountPath: /usr/share/nginx/html
          name: myvolume
  volumes:
    - name: myvolume
      persistentVolumeClaim:
        claimName: mypvc # use claim
```

**Mount multiple sources in the same directory in container**

_pod_with_projected_volume.yaml_

```yaml
...
spec:
  containers:
    - name: mypod
      image: nginx
      volumeMounts:
        - name: myvolume
          mountPath: "/projected-volume"
          readOnly: true
  volumes:
    - name: myvolume
      projected:
        sources:
          - secret:
              name: user # from first secret
          - secret:
              name: pass # from second secret
```
