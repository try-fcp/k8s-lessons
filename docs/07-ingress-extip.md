# Pod with PVC


```
kubectl apply -f https://raw.githubusercontent.com/try-fcp/k8s-lessons/main/tutorial/ingres-svc.yaml
```

> output:
```
namespace/ingress-nginx created
serviceaccount/ingress-nginx created
configmap/ingress-nginx-controller created
clusterrole.rbac.authorization.k8s.io/ingress-nginx created
clusterrolebinding.rbac.authorization.k8s.io/ingress-nginx created
role.rbac.authorization.k8s.io/ingress-nginx created
rolebinding.rbac.authorization.k8s.io/ingress-nginx created
service/ingress-nginx-controller-admission created
service/ingress-nginx-controller created
deployment.apps/ingress-nginx-controller created
ingressclass.networking.k8s.io/nginx created
validatingwebhookconfiguration.admissionregistration.k8s.io/ingress-nginx-admission created
serviceaccount/ingress-nginx-admission created
clusterrole.rbac.authorization.k8s.io/ingress-nginx-admission created
clusterrolebinding.rbac.authorization.k8s.io/ingress-nginx-admission created
role.rbac.authorization.k8s.io/ingress-nginx-admission created
rolebinding.rbac.authorization.k8s.io/ingress-nginx-admission created
job.batch/ingress-nginx-admission-create created
job.batch/ingress-nginx-admission-patch created
```

To check:
```
kubectl -n ingress-nginx get svc
```

>output:
```
NAME                                 TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)                      AGE
ingress-nginx-controller             NodePort    172.18.0.107   <none>        80:30937/TCP,443:32539/TCP   21s
ingress-nginx-controller-admission   ClusterIP   172.18.0.143   <none>        443/TCP                      22s
```

Deploy sample app:

```
kubectl apply -f https://raw.githubusercontent.com/try-fcp/k8s-lessons/main/tutorial/apple.yaml
kubectl apply -f https://raw.githubusercontent.com/try-fcp/k8s-lessons/main/tutorial/banana.yaml
```
> output:
```
pod/apple-app created
service/apple-service created

pod/banana-app created
service/banana-service created
```

Config ingress route for app:

```
kubectl apply -f https://raw.githubusercontent.com/try-fcp/k8s-lessons/main/tutorial/config-ingress.yaml
```

> output:
```
ingress.networking.k8s.io/example-ingress created
```

Patch for ExternalIP

We need to determine FCP IPv6 for your kubernetes cluster first. You can find it out on your cluster status page:

```
 curl --no-progress-meter -H cid:<CID> https://try-fcp.org/api/v1/status/<CLUSTER> | grep external_ipv6
```

> output:
```
  "external_ipv6": "2a01:4f8:140:918b::9",
```

Now update the configuration of Ingress SVC for using available address for external listening:

```
kubectl patch svc ingress-nginx-controller -p '{"spec":{"externalIPs":["2a01:4f8:140:918b::9"]}}' -n ingress-nginx
```

To check:
```
kubectl -n ingress-nginx get svc
```

> output:
```
service/ingress-nginx-controller patched
```

Now your applications are available to the entire Internet! From any Internet host:

```
curl -6 http://[2a01:4f8:140:918b::9]/banana
```

> output:
```
banana
```


Next: [Lesson 8: ]()
