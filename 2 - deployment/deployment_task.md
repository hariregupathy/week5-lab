# Deployment Worksheet

__Task 2, step 6: After completing step 5 of task 2, what do you notice about the `ReplicaSet` - what is this used for?__
hint: use ` kubectcl get rs --show-labels`

```
It lists the replica set with number of replica set ready, current and desired.
Additionally, labels are shown as well that app name, environment and pod hash with the api object.

hregupathy@WFILv2-031 manifests]$ kubectl get rs --show-labels
NAME                          DESIRED   CURRENT   READY   AGE     LABELS
nginx-deployment-7b658cc6f4   2         2         2       5m36s   app.kubernetes.io/version=1.0,app_name=nginx,env=dev,pod-template-hash=7b658cc6f4

```

__Task 2, step 7: what command did you use to scale the deployment?__

```
kubectl scale --replicas=3 rs/nginx-deployment-7b658cc6f4
```

__Task 3, step 2: Why are there two replica sets but only one deployment?__

```
There are two replica sets but only one of them is active with 2 pods.  Where as the other replica
set is with 0 pod.  However, the deployment is only 1.  I belive, changing the kubernetes version in the template from 1 to 2 made
the previous rs to 0 and the new rs with 2.0 version to have the 2 replicas.  Also, the deployment is same deployment and we overwrote it
and hence only one deployment.
```

__Task 3, step 6: What command did you use to roll back the deployment?__

```
kubectl rollout undo deployment/nginx-deployment --to-revision=1
```
