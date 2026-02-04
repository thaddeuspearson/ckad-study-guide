# Environment Variables

## General Notes

<br>

## YAML Template

### env
```yaml
apiVersion: v1
kind: Pod
metadata:
    name: app-name
spec:
    containers:
      - name: container-name
        image: container-image
        ports:
          - containerPort: 8080
        env:
          - name: ENV_VAR
            value: environnment_variable
```

### configMapKeyRef
```yaml
apiVersion: v1
kind: Pod
metadata:
    name: app-name
spec:
  containers:
    - name: container-name
      image: container-image
      ports:
        - containerPort: 8080
      env:
        - name: ENV_VAR
          valueFrom:
            configMapKeyRef:
```

### secretKeyRef
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: app-name
spec:
  containers:
    - name: container-name
      image: container-image
      ports:
        - containerPort: 8080
      env:
        - name: ENV_VAR
          valueFrom:
            secretKeyRef:
```

<br>

## Commands

<br>