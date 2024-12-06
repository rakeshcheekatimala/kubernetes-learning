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