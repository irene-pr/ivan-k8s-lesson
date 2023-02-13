Kind

```bash
kind create cluster --name <name>
kind create cluster --config kind-config.yaml
kind get clusters
kind delete cluster --name <name>
```

Helm

```bash
helm create <chart, p.e. nginx-chart>
helm list -A

# the values file is values.yaml the default unless specified
helm install <new name namespace> <chart>
# the difference between upgrade vs upgrade --install is that the first just adds the changes relative to the previous version, whereas the second ¿restarts everything?
helm upgrade <new name namespace> <chart>
helm upgrade --install nginx nginx-chart
# --wait will stack the command
# --atomic if the command fails it reverts back to the last version that actually works
helm upgrade --install nginx1 nginx-chart --wait --atomic -f nginx-chart/values-staging.yaml --namespace nginx1 --create-namespace
```

Kubectl

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
