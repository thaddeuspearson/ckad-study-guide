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
              name: configmap-name
              key: APP_ENV_VAR
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
              name: app-secret
              key: base64-encoded-secret
```

or as Volume

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
      volumes:
        - name: app-secret-volume
          secret:
            secretName: app-secret-name
```
note: each secret will be mounted as a file (secret name) with the value of the secret as the file content



<br>

## Commands

<br>