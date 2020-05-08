![](https://istio.io/docs/examples/bookinfo/noistio.svg)
```bash
master $ kubectl get pod -o wide
NAME                             READY   STATUS    RESTARTS   AGE    IP           NODE     NOMINATED NODE   READINESS GATES
details-v1-c5b5f496d-xxm2c       2/2     Running   0          107s   10.40.0.13   node01   <none>           <none>
productpage-v1-c7765c886-bdl6x   2/2     Running   0          106s   10.40.0.18   node01   <none>           <none>
ratings-v1-f745cf57b-4lsqr       2/2     Running   0          107s   10.40.0.14   node01   <none>           <none>
reviews-v1-75b979578c-vqd4g      2/2     Running   0          106s   10.40.0.15   node01   <none>           <none>
reviews-v2-597bf96c8f-6smcw      2/2     Running   0          106s   10.40.0.16   node01   <none>           <none>
reviews-v3-54c6c64795-6qpkp      2/2     Running   0          106s   10.40.0.17   node01   <none>           <none>

master $ kubectl get svc -o wide
NAME          TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)    AGE   SELECTOR
details       ClusterIP   10.101.41.162    <none>        9080/TCP   17m   app=details
kubernetes    ClusterIP   10.96.0.1        <none>        443/TCP    15h   <none>
productpage   ClusterIP   10.100.240.212   <none>        9080/TCP   17m   app=productpage
ratings       ClusterIP   10.101.170.120   <none>        9080/TCP   17m   app=ratings
reviews       ClusterIP   10.102.108.56    <none>        9080/TCP   17m   app=reviews
```
