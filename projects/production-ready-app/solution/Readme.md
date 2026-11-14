# How to Run the App

## Apply the manifests

```bash
kubectl apply -f configmap.yaml
kubectl apply -f secret.yaml
kubectl apply -f deployment.yaml
```

## Wait for the rollout

```bash
kubectl rollout status deployment/orders --timeout=180s
```

## Check the pods

```bash
kubectl get pods -l app=orders
```
