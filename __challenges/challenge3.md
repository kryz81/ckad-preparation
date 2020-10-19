**Create new deployment**

1. name: nginx-deploy
2. container name: nginx
3. image: nginx:1.16
4. replicas 4

**Use rolling update strategy for the deployment**

1. maximum number of pods that can be created over the desired number of pods: 1
2. maximum number of pods that can be unavailable during the update process: 2

**Upgrade deployment and then undo**

1. new image version: 1.17
2. undo to the previous version
