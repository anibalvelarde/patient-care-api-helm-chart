# patient-care-api-helm-chart
Helm Chart Definition for Patient Care API Service

## To Create/Init A Helm Chart
```sh
 
 $ helm create <my-chart-name>

 # <my-chart-name> becomes the root directory for all your chart artifacts

```

## To Install A Helm Chart on a K8s Cluster
```sh

helm install <pod-name> ./my-chart-directory -n <your-name-space>
# if you do not specify -n, it will deploy to the default namespace

```

### Output from `install` command
Assuming your command was something like this:
```sh

$ helm install neurocorp-api ./patient-care-api -n kubeapps

```
If sucessfull, you should see something simiarl to this:
```sh
NAME: neurocorp-api
LAST DEPLOYED: Sat May 18 23:07:36 2024
NAMESPACE: kubeapps
STATUS: deployed
REVISION: 1
NOTES:
1. Get the application URL by running these commands:
  export POD_NAME=$(kubectl get pods --namespace kubeapps -l "app.kubernetes.io/name=patient-care-api,app.kubernetes.io/instance=neurocorp-api" -o jsonpath="{.items[0].metadata.name}")
  export CONTAINER_PORT=$(kubectl get pod --namespace kubeapps $POD_NAME -o jsonpath="{.spec.containers[0].ports[0].containerPort}")
  echo "Visit http://127.0.0.1:8080 to use your application"
  kubectl --namespace kubeapps port-forward $POD_NAME 8080:$CONTAINER_PORT

```

Copy the commands from that output. Remember to add the `\` to append the commands on your `git-bash` shell.  It should look like this:
```sh

  export POD_NAME=$(kubectl get pods --namespace kubeapps -l "app.kubernetes.io/name=patient-care-api,app.kubernetes.io/instance=neurocorp-api" -o jsonpath="{.items[0].metadata.name}") \
  export CONTAINER_PORT=$(kubectl get pod --namespace kubeapps $POD_NAME -o jsonpath="{.spec.containers[0].ports[0].containerPort}") \
  echo "Visit http://127.0.0.1:8080 to use your application" \
  kubectl --namespace kubeapps port-forward $POD_NAME 8080:$CONTAINER_PORT

```