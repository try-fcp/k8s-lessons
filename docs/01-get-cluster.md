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


![cluster-info screenshot](images/cluster-info.png)



Next: [Lesson 2: Configuring PVC](02-configuring-pvc.md)
