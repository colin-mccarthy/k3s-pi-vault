
## secretKeyRef
[docs](https://kubernetes.io/docs/concepts/configuration/secret/#using-secrets-as-environment-variables)

```
          valueFrom:
            secretKeyRef:
              key: password
              name: vault-webpassword
              
```

## configMapRef
[docs]([docs](https://kubernetes.io/docs/concepts/configuration/secret/#using-secrets-as-environment-variables))

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

