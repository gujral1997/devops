## Commands

1. `kubectl get pods` Check running pods
2. `kubectl apply -f client-pod.yaml` Update existing pod
3. `kubectl describe <object type>` Detailed information about object type
4. `kubectl describe <object type> <object name>` Detailed information about object
5. `kubectl delete -f client-pod.yaml` To delete
6. `kubectl get deployments` Get existing deployments
7. `minikube ip` To get kube8 IP
8. `kubectl get pods -o wide` additional info
9. `kubectl get service` to know which service is running
10. `kubectl set image deployment/client-deployment client=gujral1997/complex-client:v1` Update deployed image
