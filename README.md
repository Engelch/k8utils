# k8utils

|     key      | value  |
| ------------ | ------ |
| version      | 0.2.3  |
| created      | 191118 |
| last updated | 191118 |

## Introduction

Wrappers for `kubectl` to simplify common tasks.

Often, I have to start a specific shell container to test for network availability of a service towards the kubernetes cluster. When doing so, to connect to this pod requires to determine its indivdual pod-name. Often, the pod name is unique or can easily be made unique.

In such a case, the script `k8exec` helps. If called with a string that uniquely identifies the pod the connection to the pod can be done using this command. Typical options such as `-it` can be omitted. So, to connect to my centos testing image, I usually use the command:

```bash
k8exec centos
```

and voila, I am in the pod with a bash sesssion. The specified argument is handled as a case-insensitive string. Here is an example call:

```bash
hadm@d-prj1-k8s-ctrl|13|~$./k8exec centos
[root@centos-extd-6c6f84887f-zp4xm /]#
```

More information about the application, a bash shell-script, can be obtained by

```bash
k8xec -h
```

The actual issued command is created from the command of this scripts. So if the command is `k8exec` then the issued command is **kubectl exec**. If the command is `k8logs` then the command will be **kubectl logs**. This can easily be extended for further commands.

The implementation of `k8logs` also supports the `-f` option (`tail -f` mode).
