# ReplicaSet Worksheet:

__Task 1, step 7: Enter the command you used for scaling the replica set:__
```
kubectl scale --replicas=3 rs/nginx-replica
```

__Task 1, step 9: What happened after applying another pod with matching selectors as the ReplicaSet?__
```
One of the existing pod was delted and a new one brought up.  Based on the rs events it appears the overall replicas of 3 
is maintained throughout the deployment of replica_2.yml deployment.
```
