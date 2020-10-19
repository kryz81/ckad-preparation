### Taints and tolerations

**Use CLI to taint a node**

```shell script
kubectl taint nodes node01 tier=backend:NoSchedule
```


**Add toleration to pod**

```yaml
...
spec:
  tolerations:
  - key: "example-key"
    operator: "Exists"
    effect: "NoSchedule"
```
