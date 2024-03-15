# StatefulSet Worksheet

__Task 5, step 3: Describe what happened and what you noticed about the pods and the volumes for them.__

```
The stateful set pods are created.  3 statefulsets were created, and 3 persistent volumes were 
created with each of 100M and then a Persistent volume claim was made on the created PV.
```

__Task 5, step 4: Did anything change? Why or why not?__

```
Nothing changed after updating the stateful_1.yml with api version 2.0 because the update strategy is set "OnDelete"
So the 2.0 version is not reflected immediately and will not do so until the current pods are manually deleted.
```

__Task 5, step 6: What happened and why?__

```
As expected, after manual deletion of one pod, the newer pod that cameup was with api version 2.0

[hregupathy@WFILv2-031 manifests]$ kubectl get pods --show-labels
NAME               READY   STATUS    RESTARTS   AGE    LABELS
stateful-nginx-0   1/1     Running   0          21m    app.kubernetes.io/version=1.0,app_name=sts-nginx,apps.kubernetes.io/pod-index=0,controller-revision-hash=stateful-nginx-759c5bbb79,statefulset.kubernetes.io/pod-name=stateful-nginx-0
stateful-nginx-1   1/1     Running   0          21m    app.kubernetes.io/version=1.0,app_name=sts-nginx,apps.kubernetes.io/pod-index=1,controller-revision-hash=stateful-nginx-759c5bbb79,statefulset.kubernetes.io/pod-name=stateful-nginx-1
stateful-nginx-2   1/1     Running   0          2m5s   app.kubernetes.io/version=2.0,app_name=sts-nginx,apps.kubernetes.io/pod-index=2,controller-revision-hash=stateful-nginx-655cdf85b,statefulset.kubernetes.io/pod-name=stateful-nginx-2

```

__Task 5, step 9: What happens this time?__

```
Since the update strategy is rollingupdate, the api version changed immediately to 3.0

hregupathy@WFILv2-031 manifests]$ kubectl get pods --show-labels
NAME               READY   STATUS    RESTARTS   AGE   LABELS
stateful-nginx-0   1/1     Running   0          12s   app.kubernetes.io/version=3.0,app_name=sts-nginx,apps.kubernetes.io/pod-index=0,controller-revision-hash=stateful-nginx-7c74995ff7,statefulset.kubernetes.io/pod-name=stateful-nginx-0
stateful-nginx-1   1/1     Running   0          14s   app.kubernetes.io/version=3.0,app_name=sts-nginx,apps.kubernetes.io/pod-index=1,controller-revision-hash=stateful-nginx-7c74995ff7,statefulset.kubernetes.io/pod-name=stateful-nginx-1
stateful-nginx-2   1/1     Running   0          16s   app.kubernetes.io/version=3.0,app_name=sts-nginx,apps.kubernetes.io/pod-index=2,controller-revision-hash=stateful-nginx-7c74995ff7,statefulset.kubernetes.io/pod-name=stateful-nginx-2

```

__Task 5, step 11: Repeat step 10. Was everything deleted? Why or why not?__

```
a)  There was pods, sts, pvc and pv present.
b)  after running kubectl delete sts stateful-nginx, the pods and statefulset is deleted, however, the PVC and PV remain as expected.
```