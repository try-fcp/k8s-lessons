# Pod with PVC

Let's complicate the previous example and start the Pod with nginx service 
using a shared volume on which we will place an arbitrary file.

```
kubectl apply -f https://raw.githubusercontent.com/try-fcp/k8s-lessons/main/tutorial/nginx-pv-pod.yaml
```

> output:
```
pod/nginx-pv-pod created
```

FCP provides access to your PV via scp/ssh (other method is WIP) via jail console.

Log into it using your key:

```
ssh -4 fcp@23.88.72.108 -p2048
```

> output:
```
cluster-info:
Kubernetes control plane is running at https://[2a01:4f8:272:5cee::4]
CoreDNS is running at https://[2a01:4f8:272:5cee::4]/api/v1/namespaces/kube-system/services/coredns:dns/proxy

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.
get nodes -o wide:
NAME      STATUS   ROLES           AGE   VERSION   INTERNAL-IP   EXTERNAL-IP   OS-IMAGE             KERNEL-VERSION     CONTAINER-RUNTIME
master1   Ready    master,worker   29m   v1.23.2   172.16.0.2    <none>        Ubuntu 20.04.3 LTS   5.4.0-96-generic   containerd://1.5.9
get pv:
NAME     CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS   CLAIM               STORAGECLASS   REASON   AGE
nfs-pv   20Gi       RWX            Recycle          Bound    default/fileshare                           29m

Type 'k9s' to rub K9S
```

a 'pv' directory in your home directory is the root of the server. Let's create an index file with arbitrary content, e.g.:
```
echo "Welcome to FCP" > ~/pv/index.html
```

Now use port-forwarding to nginx-pv-pod:80 as we did in the previous lesson and try to open our index file on PV:

```
kubectl port-forward nginx-pv-pod 1080:80
```

```
curl http://localhost:1080
```

> output:
```
Welcome to FCP
```



Next: [Lesson 7: ]()
