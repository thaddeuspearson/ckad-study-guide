# Readiness Probes

## General Notes

- a method to ensure a Pod's status is only changed to `Ready` based on the state of the application running inside of the container
- Several types of probes:
    - HTTP test
    - TCP Test
    - Exec Command

<br>

## YAML Template

### HTTP Probe
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod-name
  labels: 
    name: pod-name
spec:
  contatiners:
  - name: app-name
    image: image-name
    ports:
    - containerPort: 8080
    readinessProbe:
      httpGet:
        path: /api/ready
        port: 8080
    livenessProbe:
      httpGet:
        path: /api/ready
        port: 8080
```

### TCP Probes
```yaml
...
    readinessProbe:
      tcpSocket:
        port: 3306
    livenessProbe:
      tcpSocket:
        port: 3306
```

### Exec Command Probes
```yaml
...
    readinessProbe:
      exec:
        command:
          - cat
          - /app/is_ready
    livenessProbe:
      exec:
        command:
          - cat
          - /app/is_ready
```
<br>

## Commands

<br>