# k3s-fch


cd ./argocd/apps/argocd/
helm dependency build

cd ../../..
helm install argo-cd ./argocd/apps/argocd --namespace argocd --create-namespace

https://argo-cd.k3s-fch.dev.gnc/
user : admin
password : `kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 -d`

cd ./argocd/apps/apps_of_apps/
helm dependency build
helm install apps-of-apps ./argocd/apps/apps_of_apps