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