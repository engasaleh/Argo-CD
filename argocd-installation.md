# File: deploy-argocd.md

# Deploy Argo CD to Kubernetes

## Use the terminal to deploy Argo CD:

```bash
helm repo add argo https://argoproj.github.io/argo-helm
helm repo update
helm upgrade --install argocd argo/argo-cd --set-string configs.params."server\.disable\.auth"=true --version 7.1.1 --create-namespace -n argocd
```


# Accessing Argo CD UI and Retrieving Admin Password

After reaching the Argo CD UI for the first time, you can log in using the default **username**:  


The **password** is randomly generated during installation. To retrieve it, run the following command:

```bash
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

- Here, you maybe need a privilage, so you will use "sudo"
# Install ArgoCD CLI:-

```bash
curl -sSL -o /usr/local/bin/argocd https://github.com/argoproj/argo-cd/releases/download/v2.11.2/argocd-linux-amd64
chmod +x /usr/local/bin/argocd
```

# Deleting the Initial Admin Secret
For security reasons, it is recommended to delete the initial secret after retrieving the password. Run:
```bash
kubectl -n argocd delete secret argocd-initial-admin-secret
```
