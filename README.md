# Freebernetes Cloud Platform

This guide covers some of the use cases for setting up and using the open Freebernetes cloud. The tutorial are not Freebernetes cloud specific as the user is working with a vanilla kubernetes installation.
However, the examples are adapted, tested and applied to the current Freebernetes  platform.

these pages are designed and optimized for learning how to use Kubernetes cluster and use Feebernetes cloud as the most accessible way to try kubernetes.

> The results of this tutorial should not be viewed as production ready, and may receive limited support from the community, but don't let that stop you from learning!

## FCP free plan Cluster layout details

The Freebernetes cloud allows you to get a free installation of Kubernetes for a short period of time. Since the cloud is fully funded by the community (crowdfunding model), restrictions and limits may change every month.

Current restriction:

* 1 single master + worker node;
* 1 master + 2 worker node;
* Single NFS based PV;
* External IPv6 address per cluster;

Components:

* [kubernetes](https://github.com/kubernetes/kubernetes) v1.21.0+
* [containerd](https://github.com/containerd/containerd) v1.4.4+
* [coredns](https://github.com/coredns/coredns) v1.8.3+
* [cni](https://github.com/containernetworking/cni) v0.9.1+
* [etcd](https://github.com/etcd-io/etcd) v3.4.15+

## Labs

This tutorial assumes you use Freebernetes cloud [Freebernetes Cloud Platform](https://XXX) (free plan).

For the begginers:

* [Lesson 1: Get cluster](docs/01-get-cluster.md)
* [Lesson 2: Configuring PVC](docs/02-configuring-pvc.md)
* [Lesson 3: Pod deployment](docs/03-pod-deployment.md)
* [Lesson 4: Exec and run Pod command](docs/04-pod-exec.md)
* [Lesson 5: Pod port exposing](docs/05-pod-port-exposing.md)
* [Lesson 6: Pod with PVC](docs/06-pod-pvc.md)
* [Lesson X: Configure Ingress on externalIP](docs/05-ingress-extip.md)
* [Lesson X: Configure Balancer (metalb) on externalIP](docs/06-metalb-extip.md)
* [Lesson X: Configure Ingress behind the Balancer on ExrnalIP](docs/07-ingress-metalb-extip.md)
* [Lesson X: Configure Dashboard](docs/08-ingress-metalb-extip.md)
* [Lesson X: Configure VictoriaMetrics/Grafana stack](docs/09-victoriametrics-grafana.md)
* [Lesson X: Pod scaling](docs/10-pod-scaling.md)
* [Lesson X: Debugging/events](docs/11-debug-events.md)
* [Lesson X: ...](docs/12-debug-events.md)
...

For advanced users:

ITSIO, Kiali.io, ...

