# CronJob

## General Notes
- a Job that can be scheduled
- takes a cron string to specify when to schedule the job
<br>

## YAML Template
```yaml
apiVersion: batch/v1beta1
kind: CronJob
metadata:
  name: <cron-job-name>
spec:
  schedule: "*/1 * * * *"
  jobTempalte:
    spec:
      completions: <num-of-job-pods-desired>
        parallelism: <num-of-parallel-job-pods-desired>
        template:
          spec:
            containers:
            - name: <container-name>
              image: <container-image>
              restartPolicy: Never
```
_note: there are 3 `spec` sections in the template_
<br>

## Commands

### create CronJob
```
kubectl create -f cron-job-definition.yaml
```

### get CronJob
```
kubectl get cronjob
```
<br>