**Create deployment**

1. name: redis
2. image: redis:alpine
3. replicas: 1
4. container cpu request: 0.2
5. pod label: app=redis
6. container exposes port 6379

**Mount volumes**

1. empty dir "data" on "/mnt/data", which survives pod crash/restart

**Deploy on node**

1. Make sure pod is deployed on "master" node
