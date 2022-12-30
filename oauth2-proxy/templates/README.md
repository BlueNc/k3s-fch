./oauth2-proxy/templates/secret.yaml
```
apiVersion: v1
kind: Secret
metadata:
  name: oauth2-proxy-secret
  annotations:
    sealedsecrets.bitnami.com/cluster-wide: "true"
data:
  cookie-secret: <openssl rand -base64 32 | head -c 32 | base64>
  client-secret: <echo -n "****" | base64>
  client-id: <echo -n "****" | base64>
  ```

  kubeseal -f ./oauth2-proxy/templates/secret.yaml --format yaml > ./oauth2-proxy/templates/secret-sealed.yaml