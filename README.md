# Joomla GitOps — Argo CD App of Apps

Repository layout:

```text
argocd/
  root.yaml
  applications/
    joomla.yaml
    mariadb.yaml
apps/
  joomla/
  mariadb/
```

## Bootstrap

Argo CD must already be installed.

Push this repository to:

`https://github.com/tabbi/joomla-gitops.git`

Then create only the root application manually:

```bash
kubectl apply -f argocd/root.yaml
```

The root application creates the `joomla` and `mariadb` Argo CD Applications.
Those applications deploy their workloads into the `joomla` namespace.

## Check

```bash
kubectl get applications -n argocd
kubectl get all -n joomla
kubectl get pvc -n joomla
```

## Open Joomla locally

```bash
kubectl port-forward -n joomla svc/joomla 8081:80
```

Open:

`http://localhost:8081`

## Lab warning

The MariaDB passwords are deliberately stored as a plain Kubernetes Secret for
local lab use. Do not use this secret-management approach for production.
