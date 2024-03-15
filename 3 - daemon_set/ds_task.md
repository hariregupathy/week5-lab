# DaemonSet Worksheet


__Task 4, step 5: Once you apply the DaemonSet, what happens and why?__

```
daemonset.apps/nginx-ds created
As soon as it is applied, the Daemonset is created.  However, no pods were found in the default namespace
It was created because we asked it to create a health type Daemonset.
There were 0 pods because there were no node labled as 'health' in the cluster
```

__Task 4, step 7: What happened when you labeled the node and why?__

```
After labeling a node using minikube to health, the Daemonset pod came up in the default ns.

hregupathy@WFILv2-031 manifests]$ kubectl label node minikube nodeType=health
node/minikube labeled
[hregupathy@WFILv2-031 manifests]$ kubectl get pods
NAME             READY   STATUS    RESTARTS   AGE
nginx-ds-kzmsw   1/1     Running   0          5s

```