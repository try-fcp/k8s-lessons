# PV

By default, a Freebernetes cluster comes with one NFSv4-based PV named 'nfs-pv' with a quota of 20Gi:

```
kubectl get pv
```

> output

```
NAME     CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS      CLAIM   STORAGECLASS   REASON   AGE
nfs-pv   20Gi       RWX            Recycle          Available                                   54s
```

## PVC

An example of creating an arbitrary PVC named 'fileshare' on the 'nfs-pv' PV with a request of 8Gi, tutorial/fileshare-pvc.yaml:

```
---
kind: PersistentVolumeClaim
apiVersion: v1
metadata:
  name: fileshare
spec:
  accessModes:
  - ReadWriteMany
  resources:
    requests:
      storage: 8Gi
```

```
kubectl apply -f https://raw.githubusercontent.com/try-fcp/k8s-lessons/main/tutorial/fileshare-pvc.yaml
persistentvolumeclaim/fileshare created

kubectl get pvc
NAME        STATUS   VOLUME   CAPACITY   ACCESS MODES   STORAGECLASS   AGE
fileshare   Bound    nfs-pv   20Gi       RWX                           3s
```


Next: [Lesson 3: Pod deployment](03-pod-deployment.md)
