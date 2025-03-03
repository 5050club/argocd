# argocd

https://argo-cd.readthedocs.io/en/stable/operator-manual/installation/

- Going with multi-tenancy over core because no UI, api, cli in core
- installed kustomize `brew install kustomize` but actually dont think I needed to because I read after that its included by default in k8s now

> kubectl create namespace argocd
> kubectl apply -n argod -f https://raw.githubusercontent.com/argoproj/argo-cd/refs/heads/master/manifests/install.yaml


To access the ArgoCD UI, you need to forward the ArgoCD server port(if you don’t use service type NodePort):
> kubectl port-forward svc/argocd-server -n argocd 7070:443

Open your browser and go to `https://localhost:8080`.  The default username is `admin`.  To get the password run:

> kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath={.data.password} | base64 -d