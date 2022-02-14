# Prerequisites

## Freeberbetes Cloud Platform

This tutorial leverages the [Freebernetes Cloud Platform](https://try-fcp.org/) with the aim of introducing and teaching elementary skills of working with Kubernetes cluster.

..

To start working with the dedicated cluster, you must send a request to create a new Kubernetes installation via the POST method:

```
{
  "init_masters": "1",
  "init_workers": "0",
  "email": "EMAIL"
}
```

To start working with free kubernetes cluster, use the [website form](https://try-fcp.org) to enter your email address and your SSH public key. To generate a new private/public key pair on a Unix-lie system ( Linux, BSD, MacOS ), use the command:
```
ssh-keygen -t ed25519
```

For example:
> ssh-keygen -t ed25519
```
ssh-keygen -t ed25519
Generating public/private ed25519 key pair.
Enter file in which to save the key (/home/k1/.ssh/id_ed25519): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/k1/.ssh/id_ed25519
Your public key has been saved in /home/k1/.ssh/id_ed25519.pub
The key fingerprint is:
SHA256:PbmDBVdG8gZI37izseJq8b8Wl4GjOEgh9kslvMHC28A k1@t495s.my.domain
The key's randomart image is:
+--[ED25519 256]--+
| o o   ...o.+    |
|  E * . .. O     |
| . B *  . +.+    |
|  . *    +o+.    |
|   o o .S.O. o   |
|    o + .o.Bo    |
|       +o =o     |
|      ......     |
|     ....oo.     |
+----[SHA256]-----+
```

Your public key is now saved in a file `~/.ssh/id_ed25519.pub`. Use the line from this file as the 'pubkey' form field:
```
cat ~/.ssh/id_ed25519.pub
```

1) copy full pubkey line, without CRLF (single line):

![pubkey](https://user-images.githubusercontent.com/98359094/153843439-65e158be-5d28-4212-b25b-e669724e40d0.png)

2) paste pubkey as in 'Pubkey' field:
 
![pubkey_form](https://user-images.githubusercontent.com/98359094/153843459-ed355ba0-bf66-4d51-8be7-7182323f39c7.png)

A confirmation will be sent to your email. Click on the link and within the next five minutes you will receive a second letter stating that your cluster has been created.

Next, install a `kubectl`, Kubernetes thin client on your system and save the `kubeconfig` from FCP email (Get kubeconfig link) to the directory ~/.kube/ as `config`. Easy way to do it:

1) create `~/.kube` directory if not exist:

```
mkdir ~/.kube
```

2) save kubeconfig as ~/.kube/config:
```
curl -H cid:c962e388f1726d16343e9de62f9e00c4 https://try-fcp.org/api/v1/kubeconfig/test1 > ~/.kube/config
```

Now you can work with your cluster directly via `kubectl` tools.

![cluster-info screenshot](images/cluster-info.png)

If it is difficult to install a thin client on your system, or you still do not have an IPv6 address, you can use the automatically created container as a jump host. How to do it: get the 'ssh_console_string' value from cluster status ( link available in FCP email ):

```
curl -H cid:c962e388f1726d16343e9de62f9e00c4 https://try-fcp.org/api/v1/status/test1
```

and use private key for accessing into jump container. Also, this container can serve for easy access to the cluster PV: pay attention to the 'pv' directory in home directory - this is the root of the cluster persistent volume.


Next: [Lesson 2: Configuring PVC](02-configuring-pvc.md)
