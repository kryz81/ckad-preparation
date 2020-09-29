### Namespaces

**Check current namespace**

```shell script
kubectl config get-contexts
```

**Set default namespace in current context**

```shell script
kubectl config set-context --current --namespace=mynamespace
```

**Create namespace using CLI**

```shell script
kubectl create ns myns
```

**Create namespace using YAML**

_ns.yaml_

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: myns
```

**Create pod in namespace using YAML**

_pod_in_ns.yaml_

```yaml
...
metadata:
  name: mypod
  namespace: myns
...
```
