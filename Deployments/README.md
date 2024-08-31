
# Deployments

A Deployment in Kubernetes is used to manage and update a group of Pods that run your application. It ensures that the right number of Pods are running at any given time and makes it easy to roll out updates, roll back to previous versions, and scale the application to handle more load.

# Key Features:
- **Declarative Updates:** You define the desired state of your application in the Deployment configuration. Kubernetes automatically adjusts the actual state to match your desired state.
- **ReplicaSets Management:** Deployments create and manage ReplicaSets, which in turn ensure that the correct number of identical Pods are running.
- **Rollback:** If an update doesn’t work as expected, you can easily roll back to a previous version of the Deployment.
- **Scaling:** Deployments allow you to scale your application up or down by simply changing the number of replicas.

# Use Cases:
- **Rolling Updates:** Gradually update your Pods to a new version without downtime.
- **Version Control:** Keep track of different versions of your application and switch between them as needed.
- **Scaling Applications:** Increase or decrease the number of running Pods to match the current demand.

### Example
Here's an example of how you can create a Deployment:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-first-deployment
spec:
  selector:
    matchLabels:
      name: my-deployment
  replicas: 3    
  template:
   metadata:
     name: web-app
     labels:
       name: my-deployment
   spec:
      containers:
        - name: nginx-container
          image: nginx   
    
```

```shell
kubectl apply -f deployment-def.yaml

```
To roll back to a previous revision of the Deployment:
```shell
kubectl rollout undo deployment/deployment-name
```
To view the update history of a Deployment: 

```shell
kubectl rollout history deployment/deployment-name

```
Pause and Resume a Rollout
```shell
kubectl rollout resume deployment/deployment-name
kubectl rollout pause deployment/deployment-name


```
* Whenever you update a Deployment in Kubernetes, it automatically creates a new ReplicaSet to manage the updated Pods, ensuring that your application remains available during the update process.

 Ref
```shell
https://kubernetes.io/docs/concepts/workloads/controllers/deployment/
```
