
## secretKeyRef

```
          valueFrom:
            secretKeyRef:
              key: password
              name: vault-webpassword
              
```

## configMapRef

```
spec:
  containers:
  - name: vault
    image: vault
    ports:
      - containerPort: 8200•
        name: vault-http
        protocol: TCP

    envFrom:
    - configMapRef:
          name: vault-vars
```

