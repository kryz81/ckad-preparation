### Service accounts

**Create service account without automounting token**

_sa_without_token.yaml_

```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: mysa
automountServiceAccountToken: false
```

**Use custom service account in pod**

_pod_with_sa.yaml_

```yaml
...
spec:
  serviceAccountName: mysa
  containers:
    - name: nginx
      image: nginx
```
