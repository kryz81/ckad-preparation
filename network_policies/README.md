### Network Policies

(!) _Some code will not work with Docker for Desktop on Mac_

**Block traffic to pod**

_block_all_traffic_to_pod.yaml_
```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: mynetworkpolicy
spec:
  podSelector:
    matchLabels:
      app: backend
  policyTypes:
    - Ingress
```

**Allow traffic to pod for ip range**

_allow_traffic_to_pod_for_ip_range.yaml_
```yaml
...
  ingress:
    - from:
        - ipBlock:
            cidr: 172.17.1.0/24
```

**Allow traffic to pod with specific label**

```yaml
...
  ingress:
    - from:
        - podSelector:
            matchLabels:
              app: backend
```
