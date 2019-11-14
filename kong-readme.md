NAME:   kong-release
LAST DEPLOYED: Mon Nov 11 13:41:03 2019
NAMESPACE: default
STATUS: DEPLOYED

RESOURCES:
==> v1/ConfigMap
NAME                                            DATA  AGE
kong-release-kong-default-custom-server-blocks  1     2s

==> v1/Job
NAME                               COMPLETIONS  DURATION  AGE
kong-release-kong-init-migrations  0/1          1s        1s

==> v1/Pod(related)
NAME                                     READY  STATUS    RESTARTS  AGE
kong-release-kong-5bf9fc94f-j8krw        0/1    Init:0/1  0         1s
kong-release-kong-init-migrations-76bpz  0/1    Init:0/1  0         1s
kong-release-postgresql-0                0/1    Pending   0         1s

==> v1/Secret
NAME                     TYPE    DATA  AGE
kong-release-postgresql  Opaque  1     2s

==> v1/Service
NAME                              TYPE       CLUSTER-IP      EXTERNAL-IP  PORT(S)                     AGE
kong-release-kong-admin           NodePort   10.105.51.101   <none>       8444:30164/TCP              2s
kong-release-kong-proxy           NodePort   10.109.197.141  <none>       80:32323/TCP,443:32380/TCP  1s
kong-release-postgresql           ClusterIP  10.109.78.60    <none>       5432/TCP                    2s
kong-release-postgresql-headless  ClusterIP  None            <none>       5432/TCP                    2s

==> v1beta2/Deployment
NAME               READY  UP-TO-DATE  AVAILABLE  AGE
kong-release-kong  0/1    1           0          1s

==> v1beta2/StatefulSet
NAME                     READY  AGE
kong-release-postgresql  0/1    1s


NOTES:
1. Kong Admin can be accessed inside the cluster using:
     DNS=kong-release-kong-admin.default.svc.cluster.local
     PORT=8444

To connect from outside the K8s cluster:
     HOST=$(kubectl get nodes --namespace default -o jsonpath='{.items[0].status.addresses[0].address}')
     PORT=$(kubectl get svc --namespace default kong-release-kong-admin -o jsonpath='{.spec.ports[0].nodePort}')


2. Kong Proxy can be accessed inside the cluster using:
     DNS=kong-release-kong-proxy.default.svc.cluster.localPORT=443To connect from outside the K8s cluster:
     HOST=$(kubectl get nodes --namespace default -o jsonpath='{.items[0].status.addresses[0].address}')
     PORT=$(kubectl get svc --namespace default kong-release-kong-proxy -o jsonpath='{.spec.ports[0].nodePort}')