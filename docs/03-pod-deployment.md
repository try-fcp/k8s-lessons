# Using Pods

Pods are the smallest deployable computing units you can create and manage in Kubernetes.

Let's create and run a BusyBox container:

```
kubectl apply -f https://raw.githubusercontent.com/try-fcp/k8s-lessons/main/tutorial/busybox-pod.yaml
```

> output

```
pod/busybox created
```

To view your pod's state, run:

```
kubectl get pods -w
```

To exit, hit "Ctrl+C"

To view your pod's status, run:

```
kubectl get pods [-o wide]
```

> output

```
NAME      READY   STATUS    RESTARTS   AGE
busybox   1/1     Running   0          6s
```

Next: [Lesson 4: Exec and run Pod command](04-pod-exec.md)
