# Pod with PVC


```
kubectl apply -f https://raw.githubusercontent.com/try-fcp/k8s-lessons/main/tutorial/ingres-svc.yaml
```

> output:
```

```

Check:
```
kubectl -n ingress-nginx get svc
```

```
kubectl apply -f apple.yaml
kubectl apply -f banana.yaml
```
> output:
```

```

kubectl apply -f https://raw.githubusercontent.com/try-fcp/k8s-lessons/main/tutorial/config-ingress.yaml


Patch for ExternalIP

see console jail/curl

```
kubectl patch svc ingress-nginx-controller -p '{"spec":{"externalIPs":["172.16.0.14"]}}' -n ingress-nginx
```




Next: [Lesson 7: ]()
