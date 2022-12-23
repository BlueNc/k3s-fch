https://cert-manager.io/docs/configuration/ca/

cd cert-manager-config/keys/
openssl genrsa -out rootCA.key 4096
openssl req -x509 -new -nodes -key rootCA.key -sha256 -days 1024 -out rootCA.crt

ca-key-pair.yaml
```
apiVersion: v1
kind: Secret
metadata:
  name: ca-key-pair
  namespace: sandbox
data:
  tls.crt: <base64 crt>
  tls.key: <base64 key>
```

cat rootCA.crt | base64 -w0 && echo
cat rootCA.key | base64 -w0 && echo

cd ..
kubeseal -f ca-key-pair.yaml --format yaml > ca-key-pair-sealed.yaml