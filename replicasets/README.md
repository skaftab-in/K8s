# ReplicaSets

A **ReplicaSet** is a higher-level abstraction that ensures a specified number of pod replicas are running at any given time. It manages the lifecycle of pods, ensuring that the desired number of replicas are always up and running.

## Key Characteristics of a ReplicaSet:
- **Maintains a Stable Set of Replicas:** The main purpose of a ReplicaSet is to maintain a stable set of replica pods running at any given time.
- **Selector:** A ReplicaSet uses a selector to identify which pods it manages. It only monitors and manages the pods matching its selector like matchlabels.
- **Scalability:** ReplicaSets allow you to scale your application easily by changing the number of replicas.
- **Scale-exisiting-pod** The best part about ReplicaSets is we can apply replication on existing pods,we just need to select the selector.

## Example: ReplicaSet Definition File (Nginx)

Here’s a simple example of a Kubernetes ReplicaSet YAML file that runs an Nginx container with three replicas:

```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: first-replicaset
spec:
  selector:
    matchLabels:
      name: web-app
  replicas: 3
  template:
    metadata:
      name: my-pod
      labels:
        name: web-app
    spec:
      containers:
        - name: nginx-server
          image: nginx


```shell
$ kubectl apply -f repli-def.yaml
``` 
To apply on existing pod

```shell
$ kubectl replace -f repli-def.yaml
```
or
```shell
$ kubectl apply -f repli-def.yaml
$ kubect scale --replicas=6 -f repli-def.yaml
```

Ref.

```shell
https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands
```


