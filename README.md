# Freebernetes Cloud Platform

This guide covers some of the use cases for setting up and using the open **Freebernetes Cloud**. The tutorials are not specific to the Freebernetes Cloud as the user is working with a standard _Kubernetes_ installation. However, the examples are adapted to, tested on and applied to the current Freebernetes platform.

These lessons are designed and optimized for learning to use a Kubernetes cluster and to use the Feebernetes Cloud as the most accessible way to try out and get started with Kubernetes.

> The results of this tutorial should not be viewed as production ready, and may receive limited support from the community, but don't let that stop you from learning!

## FCP free plan Cluster layout details

The Freebernetes Cloud allows you to get a _free_ installation of Kubernetes _for a short period of time_. Since the cloud is fully funded by the community (crowdfunding model), restrictions and limits may change every month.

Current restrictions:

* 1 single master + worker node
* 1 master + 2 worker node
* Single NFS-based PV
* 1 external IPv6 address per cluster

Components:

* [kubernetes](https://github.com/kubernetes/kubernetes) v1.23.3+
* [containerd](https://github.com/containerd/containerd) v1.5.9+
* [coredns](https://github.com/coredns/coredns) v1.8.6+
* [cni](https://github.com/containernetworking/cni) v1.0.1+
* [etcd](https://github.com/etcd-io/etcd) v3.5.1+

## Labs

This tutorial assumes you use the Freebernetes Cloud [Freebernetes Cloud Platform](https://try-fcp.org) (free plan).

For beginners:

* [Lesson 1: Get cluster](docs/01-get-cluster.md)
* [Lesson 2: Configuring PVC](docs/02-configuring-pvc.md)
* [Lesson 3: Pod deployment](docs/03-pod-deployment.md)
* [Lesson 4: Exec and run Pod command](docs/04-pod-exec.md)
* [Lesson 5: Pod port exposing](docs/05-pod-port-exposing.md)
* [Lesson 6: Pod with PVC](docs/06-pod-pvc.md)
* [Lesson 7: Configure Ingress on externalIP](docs/07-ingress-extip.md)
* [Lesson X: Configure Balancer (metalb) on externalIP](docs/08-metalb-extip.md)
* [Lesson X: Configure ConfigMaps](docs/09-metalb-extip.md)
* [Lesson X: Configure Ingress behind the Balancer on ExrnalIP](docs/07-ingress-metalb-extip.md)
* [Lesson X: Configure Dashboard](docs/08-ingress-metalb-extip.md)
* [Lesson X: Configure VictoriaMetrics/Grafana stack](docs/09-victoriametrics-grafana.md)
* [Lesson X: Pod scaling](docs/10-pod-scaling.md)
* [Lesson X: Debugging/events](docs/11-debug-events.md)
* [Lesson X: ...](docs/12-debug-events.md)
...

For advanced users:

ITSIO, Kiali.io, ...
