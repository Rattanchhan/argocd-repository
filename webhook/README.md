### 1. Generate a Shared Webhook Secret
Generate a secure random string to authenticate payload requests between GitHub and ArgoCD:
openssl rand -hex 20

### 2. Add the Secret to ArgoCD Kubernetes Cluster
Update ArgoCD's API server secret (argocd-secret) with your generated string.
Run the following command, replacing <YOUR_SECRET_STRING> with your generated string:
kubectl patch secret argocd-secret -n argocd \
  -p '{"stringData": {"webhook.github.secret": "<YOUR_SECRET_STRING>"}}'