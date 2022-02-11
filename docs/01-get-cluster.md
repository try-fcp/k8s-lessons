# Overview

This section introduces the reader to Kubernetes and the [Freebernetes Cloud Platform (FCP)](https://try-fcp.org/).

# What's Kubernetes?

Kubernetes is an open-source tool suite for managing operating system containers. Kubernetes integrates with any container software using the 
[Container Runtime Interface](https://kubernetes.io/docs/concepts/architecture/cri/). The two most popular options are
[Docker](https://www.docker.com/) and [containerd](https://containerd.io/).

## Architecture

Kubernetes organizes its components into a metaobject called a **cluster**. Kubernetes clusters have two layers:

* Nodes
* Control Plane

The control plane does several things:

* It manages all cluster data
* It schedules unassigned pods to run on nodes
* It sends requests to the API server, which fulfills actions

Although the API server is in control plane, it's easier to understand as a separate quasi-layer. It hosts the Kubernetes [REST](https://en.wikipedia.org/wiki/REST) API, which contains resources for cluster objects
and operations. The API acts on requests sent to it either directly or through control plane tools. You can extend the API by adding custom resources too. This allows you to define new Kubernetes objects, which
you can learn more about [here](https://kubernetes.io/docs/concepts/overview/working-with-objects/kubernetes-objects/).

## Use Cases

Kubernetes is useful for managing microservices: an application model that distributes its components across many containers. It allows for redundancy and scalability, 
which is why large [Software as a Service (SaaS)](https://www.investopedia.com/terms/s/software-as-a-service-saas.asp) platforms often deploy their products as microservices. 

# Freeberbetes Cloud Platform

The Freebernetes Cloud Platform is a Kubernetes API that offers free access under certain [conditions](https://github.com/olevole/fcp/blob/main/README.md#fcp-free-plan-cluster-layout-details). 

To get started, send a JSON request using curl to the Freebernetes Cloud Platform API. The JSON request specifies the parameters for our Kubernetes cluster.
This is a sample request:

```json
{
      "init_masters": "1",
      "init_workers": "2",
      "master_vm_ram": "4g",
      "master_vm_cpus": "2",
      "master_vm_imgsize": "20g",
      "worker_vm_ram": "16g",
      "worker_vm_cpus": "8",
      "worker_vm_imgsize": "20g",
      "pv_enable": "512g",
      "email": "bob@sample.com"
}
```

This code is doing three things:

* It's creating three nodes: one master, two workers
* It's setting virtual machine RAM, CPU cores, and container image sizes for both master and worker virtual machines
* It's statically provisioning 512 GB of [Persistent Volume (PV)](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) storage 

After you create your JSON file, send it to the FCP API using curl:

```bash
curl -X POST -H "Content-Type: application/json" -d @my-cluster.json https://try-fcp.org/api/v1/create/test1
```

This command sends your JSON file, my-cluster.json, as a POST request to the "create" endpoint of the FCP API. You may set the parameter "test1" to whatever name you want for your Kubernetes cluster.

<!--![cluster-info screenshot](images/cluster-info.png)-->

Next: [Lesson 2: Configuring PVC](02-configuring-pvc.md)
