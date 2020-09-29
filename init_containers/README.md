### Liveness and readiness probes

**Add init container to pod**
```yaml
...
spec:
  containers:
    - name: nginx
      image: nginx
  initContainers: # must finish, then main containers will run
    - name: sleep
      image: alpine
      args:
        - sleep
        - "15"  
```
