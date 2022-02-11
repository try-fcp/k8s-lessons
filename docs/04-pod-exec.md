# Exec and run commands

`kubectl exec` executes a given command in a container. For example, we can run nslookup on Google in our busybox container:

```
kubectl exec -ti busybox -- nslookup google.com
```

> output

```
Server:         172.18.0.2
Address:        172.18.0.2:53

Non-authoritative answer:
Name:   google.com
Address: 2a00:1450:4001:812::200e
```

If the container has a shell interpreter, 
run this command to enter the container:


```
kubectl exec -ti busybox -- sh
```

> output prompt

```
/ #
```

To create a container called "my-shell" with a bash prompt from the `ubuntu` image, we use the run command:
```
kubectl run my-shell --rm -i --tty --image ubuntu -- bash
```

Hint: You can regulate restart policy via `--restart` args, e.g: `--restart=Never`, `--restart=always` ...
Hint:  while the command is being executed, the container will run and you can attach in parallel via:
```
kubectl attach my-shell -c my-shell -i -t
```

Next: [Lesson 5: Pod port forwarding](05-pod-port-forwarding.md)
