## Kind

```bash
kind create cluster --name <name>
kind create cluster --config kind-config.yaml
kind get clusters
kind delete cluster --name <name>
```

## Helm

```bash
helm create <chart, p.e. nginx-chart>
helm list -A

# the values file is values_1.yaml the default unless specified
helm install <new name namespace> <chart>
# the difference between upgrade vs upgrade --install is that the first just adds the changes relative to the previous version, whereas the second ¿restarts everything?
helm upgrade <new name namespace> <chart>
helm upgrade --install nginx nginx-chart
# --wait will stack the command
# --atomic if the command fails it reverts back to the last version that actually works
helm upgrade --install nginx1 nginx-chart --wait --atomic -f nginx-chart/values_2.yaml --namespace nginx1 --create-namespace
```

### Ingress NGINX

Docs link: https://kubernetes.github.io/ingress-nginx/

```bash
helm upgrade --install ingress-nginx YourPathToTheChart\...\ingress-nginx --set controller.service.type="NodePort" --set controller.service.nodePorts.http=30000 --namespace ingress-nginx --create-namespace --wait --atomic
```

### Helm Install NGINX1 & NGINX2

```
helm install nginx1 nginx-chart --namespace nginx1 --create-namespace --values .\nginx-chart\values_1.yaml
```

```
helm install nginx2 nginx-chart --namespace nginx2 --create-namespace --values .\nginx-chart\values_2.yaml
```

## Kubectl

```bash
kubectl get all
kubectl get all -n <namespace>
kubectl get [namespaces, ns]

kubectl apply -f <manifest path>

kubectl delete pod/<pod>
kubectl delete -f <manifest path>

kubectl describe pod <pod>
kubectl describe service/<service>

kubectl config get-contexts

kubectl port-forward pod/<pod> <port>:<port>
```

## Install keycloak

```
helm upgrade --install keycloak keycloak-chart --namespace keycloak --create-namespace --wait --atomic
```

## Install ArgoCD

```
helm upgrade --install argocd argocd-chart --namespace argocd --create-namespace --wait --atomic
```

get password
```
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}"
```
