# Persistent Volumes

Learn about Persistent Volumes (PVs) [here](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)

<div class="alert alert-info" role="alert">
    This tutorial uses the `kubectl` tool frequently to control the cluster manager. Learn more [here](https://kubernetes.io/docs/reference/kubectl/kubectl/) if you've never used it
</div>

Freebernetes clusters have one NFSv4-based Persistent Volume named "nfs-pv" with a quota of 20 gigabytes. To view this PV, run:

```
kubectl get pv
```

> output

```
NAME     CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS      CLAIM   STORAGECLASS   REASON   AGE
nfs-pv   20Gi       RWX            Recycle          Available                                   54s
```

## Persistent Volume Claims

Persistent Volume Claims (PVCs) are how users request storage. 
Let's make a Persistent Volume Claim named "fileshare" on the "nfs-pv" PV for 8 gigabytes and save it to `fileshare-pvc.yaml`:

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

To apply this file to your Kubernetes pod, run:

```
kubectl apply -f fileshare-pvc.yaml
```

> output
```
persistentvolumeclaim/fileshare created
```

To check the status of your PVC, run:
```
kubectl get pvc
```

> output
```
NAME        STATUS   VOLUME   CAPACITY   ACCESS MODES   STORAGECLASS   AGE
fileshare   Bound    nfs-pv   20Gi       RWX                           3s
```

Next: [Lesson 3: Pod deployment](03-pod-deployment.md)
