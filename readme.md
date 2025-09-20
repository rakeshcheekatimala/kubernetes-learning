Replicaset Template

```
apiVersion: apps/v1
kind: ReplicaSet
metadata:
    name: {{value}}
    labels:
        app: {{value}}
spec:
    template:
        metadata:
            labels:
                app: {{value}}
        spec:
            containers:
                - name: {{value}}
                image: {{value}}
    replicas: 3
    selector:
        matchLabels:
         app: {{value}}
            
```

Service Template

```
apiVersion: v1
kind: Service
metadata:
    name: {{}}
    labels:
        app: {{}}
spec:
    type: {{}}
    ports:
        - port: {{}}
          targetPort: {{}}
          nodePort: {{}}
    selector:
        name: {{}}
```

NodePort range is 30000 to 32767 

Default type is ClusterIp

port is mandatory, targetPort if skipped will be same as port. 


Exposed Service Url

minikube service myapp-service --url 

# Create pod defintion for the inline image 

```
    kubectl run redis --image=redis --dry-run=client -o yaml > redis.yaml
```

Useful Tip

```
kubectl create command name --dry-run -o json/yaml
```

Output with wide (additional details):

Probably the most common format used to print additional details about the object:

To create pod in different namespace 

```
kubectl create deployment name --namespace=dev
```

To set the context for namespace 

```
kubectl config set-context $(kubectl config current-context) --namespace=dev
```

Short form of namespace is ns 

How to access service from one namespace to another namespace 

db-service.dev.svc.cluster.local

How to create pod defintion file for the image 

```
kubectl run redis --image=redis --dry-run=client -o yaml > redis-pod.yaml
```