### Ingress

Works from version 1.19

**Create ingress**

_ingress.yaml_

```yaml
...
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: myingress
spec:
  rules:
    - host: mydomain.com
      http:
        paths:
          - path: /mypath
            pathType: Prefix
            backend:
              service:
                name: myservice1
                port:
                  number: 80
          - path: /mysecondpath
            pathType: Prefix
            backend:
              service:
                name: myservice2
                port:
                  number: 8080                
```
