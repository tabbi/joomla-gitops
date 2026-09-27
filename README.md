# Joomla GitOps demo

Local Joomla + MariaDB deployment managed by Argo CD.

## 1. Push this repository

Create a Git repository and push these files. Then edit `argocd/application.yaml` and replace:

`https://github.com/YOUR-USER/joomla-gitops.git`

with your repository URL.

## 2. Create the Argo CD Application

```bash
kubectl apply -f argocd/application.yaml
```

## 3. Check deployment

```bash
kubectl get applications -n argocd
kubectl get all -n joomla
kubectl get pvc -n joomla
```

## 4. Open Joomla locally

```bash
kubectl port-forward -n joomla svc/joomla 8081:80
```

Open http://localhost:8081

## Demo credentials

MariaDB database: `joomla`
MariaDB user: `joomla`
MariaDB password: `joomlapassword`

> The Secret is intentionally stored in plain text for this local lab. Do not use this pattern for production secrets.
