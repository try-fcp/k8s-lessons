# Pod port forwarding

> do not confuse with `port exposing`

You can do a port forward within the `kubetctl` utility and access to POD/service port from your localhost.
For example, let's start a container with ngink and try to open it on localhost:


```
kubectl run nginx --image=nginx --port=80 --restart=Never
```

> output

```
pod/nginx created
```

```
kubectl get pods
```

> output

```
nginx     1/1     Running   0             17s    172.17.2.5   master1   <none>           <none>
```

```
kubectl port-forward nginx 1080:80
```

> output

```
Forwarding from 127.0.0.1:1080 -> 80
Forwarding from [::1]:1080 -> 80
```

Now we have an open local `1080` port on v4/v6 loopback interfaces. Try to get something out of it:

```
curl http://localhost:1080
```

> output

```
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```


Next: [Lesson 6: Pod with PVC](06-pod-pvc.md)
