# Job

## General Notes
- designed for workloads that live for a short period of time _(ex: batch processing, data analysis, file generation etc)_
- to run multiple pods of the same job, use `completions`
- to run multiple jobs in parallel, instead of the sequential default, use `parallelism` and set the number to the desired number of jobs allowed to be run in parallel.

<br>

## YAML Template

```yaml
apiVersion: batch/v1
kind: Job
metadata:
  name: job-name
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
<br>

## Commands

### create Job
```
kubectl create -f job-definition.yaml
```

### get Job
```
kubect get jobs
```
<br>