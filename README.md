# k3s-fch


cd ./argocd/helm-chart/
helm dependency build

cd ../..
helm install argo-cd ./argocd/helm-chart --namespace argocd --create-namespace

https://argo-cd.k3s-fch.dev.gnc/
user : admin
password : `kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 -d`
