### Liveness and readiness probes

**Add liveness probe to pod**
```yaml
...
spec:
  containers:
    - name: nginx
      image: nginx
      livenessProbe:
        initialDelaySeconds: 10 # wait 10 seconds with probe start
        periodSeconds: 5 # run check every 5 seconds
        timeoutSeconds: 2 # probe timeout after 2 seconds
        failureThreshold: 5 # give up probing after 5 times
        exec:
          command:
            - cat
            - /usr/share/nginx/html/index.html
```

**Add HTTP liveness probe to pod**
```yaml
...
      livenessProbe:
        httpGet:
          port: 80
          path: /
```
