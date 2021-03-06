### Jobs

**Create job**
```yaml
apiVersion: batch/v1
kind: Job
metadata:
  name: myjob
spec:
  completions: 6 # job must be completed 3 times
  parallelism: 2 # 2 instances can be run
  backoffLimit: 2 # if instance failed, try twice before failing the job
  activeDeadlineSeconds: 120 # terminate the whole job after 120 seconds, no matter is some pods are still running
  template:
    spec:
      restartPolicy: Never
      containers:
        - name: sleep
          image: alpine
          args:
            - sleep
            - "10"
```

**Pause job**

```yaml
apiVersion: batch/v1
kind: Job
metadata:
  name: myjob
spec:
  parallelism: 0 # set parallelism to 0
```
