### Labels, selectors, annotations

**Use node selector to assign pod to specific node**

_pod_on_node.yaml_

```yaml
...
spec:
  nodeSelector:
    tier: backend
  containers:
    - name: nginx
      image: nginx
```

**Add label to node**

```shell script
kubectl label node mynode tier=backend
```

**Delete label from node**

```shell script
kubectl label node mynode tier-
````

**Select resource with specific label value**

```shell script
kubectl get po -l app=backend
```

**Show resource labels in the list**

```shell script
kubectl get all --show-labels
```
