# Exec and run Pod command

`kubectl exec` allows you to execute a command in a container. Try to exec 'nslookup' command
in busybox container:

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
you can use this command to enter the container, e.g. try to login into busybox:


```
kubectl exec -ti busybox -- sh
```

> output prompt

```
/ #
```

Another example: run `my-shell` container from `ubuntu` image and execute `bash`
```
kubectl run my-shell --rm -i --tty --image ubuntu -- bash
```

Hint: You can regulate restart policy via `--restart` args, e.g: `--restart=Never`, `--restart=always` ...
Hint:  while the command is being executed, the container will run and you can attach in parallel via:
```
kubectl attach my-shell -c my-shell -i -t
```


Next: [Lesson 5: Pod port forwarding](05-pod-port-forwarding.md)
