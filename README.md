# hello-app-helm-chart

This is a basic helm chart to deploy hello app on rails. 

## Deployment Instructions:

```
⇒ helm install hello-app .
NAME: hello-app
LAST DEPLOYED: Sun Jun 26 18:23:17 2022
NAMESPACE: default
STATUS: deployed
REVISION: 1
NOTES:
1. Get the application URL by running these commands:
  export POD_NAME=$(kubectl get pods --namespace default -l "app.kubernetes.io/name=hello,app.kubernetes.io/instance=hello-app" -o jsonpath="{.items[0].metadata.name}")
  export CONTAINER_PORT=$(kubectl get pod --namespace default $POD_NAME -o jsonpath="{.spec.containers[0].ports[0].containerPort}")
  echo "Visit http://127.0.0.1:8080 to use your application"
  kubectl --namespace default port-forward $POD_NAME 8080:$CONTAINER_PORT

```

```
helm-chart-init⚡ ⇒ kubectl get pods
NAME                         READY   STATUS    RESTARTS   AGE
hello-app-76bfb4d989-8ngqj   1/1     Running   0          8s
hello-app-76bfb4d989-mmgll   1/1     Running   0          8s
helm-chart-init⚡ ⇒ kubectl get svc 
NAME         TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)    AGE
hello-app    ClusterIP   10.99.194.16   <none>        3000/TCP   11s
kubernetes   ClusterIP   10.96.0.1      <none>        443/TCP    53m
```

```
helm-chart-init⚡ ⇒ kubectl port-forward service/hello-app 3000:3000
Forwarding from 127.0.0.1:3000 -> 3000
Forwarding from [::1]:3000 -> 3000
Handling connection for 3000
Handling connection for 3000
```
