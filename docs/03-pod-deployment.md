# Using Pods

Pods are the smallest deployable units of computing that you can create and manage in Kubernetes.

Let's create and run a busybox container

```
kubectl apply -f https://raw.githubusercontent.com/try-fcp/k8s-lessons/main/tutorial/busybox-pod.yaml
```

> output

```
pod/busybox created
```

To watch pods state:

```
kubectl get pods -w
```

( use a 'Ctrl+c' combination to exit )

To check pods status:

```
kubectl get pods [-o wide]
```

> output

```
NAME      READY   STATUS    RESTARTS   AGE
busybox   1/1     Running   0          6s
```


Next: [Lesson 4: Exec and run Pod command](04-pod-exec.md)
