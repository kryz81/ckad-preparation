### Cron jobs

**Use CLI to create a cron job**

```shell script
kubectl create cronjon mycj --image=nginx --schedule="*/5 * * * *"
````

**Create cron job using YAML**

```yaml
apiVersion: batch/v1beta1
kind: CronJob
metadata:
  name: mycj
spec:
  schedule: "*/1 * * * *"
  successfulJobsHistoryLimit: 3
  failedJobsHistoryLimit: 3
  concurrencyPolicy: Forbid # don't allow multiple concurrently running jobs  
  jobTemplate:
    spec:
      ttlSecondsAfterFinished: 300
      template:
        spec:
          restartPolicy: Never
          containers:
            - name: hello
              image: busybox
              args:
                - /bin/sh
                - -c
                - date; echo Hello from the Kubernetes cluster
```

**Allow running parallel jobs, set max. parallel jobs**

_cronjob_parallel.yaml_

```yaml
...
spec:
  schedule: "*/1 * * * *"
  concurrencyPolicy: Allow
  jobTemplate:
    spec:
      parallelism: 2
...
```
