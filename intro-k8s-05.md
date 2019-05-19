# Setting Up a Single-Node Kubernetes Cluster with Minikube

## Introduction

As we mentioned in the previous chapter, [Minikube](https://github.com/kubernetes/minikube) is the easiest and most recommended way to run an all-in-one Kubernetes cluster locally. In this chapter, we will check out the requirements to install Minikube on our workstation, as well as the installation instructions to set it up on Linux, Mac, and Windows.

![Minikube logo](assets/Minikube_logo.png){width=200 height=200px}

## Learning Objectives

By the end of this chapter, you should be able to:

- Discuss Minikube.
- Install Minikube on Linux, Mac, and Windows.
- Verify the installation.

## Requirements for Running Minikube

In most of the cases, Minikube runs inside a VM on Linux, Mac, or Windows. Therefore, we need to make sure that we have the supported hardware and the hypervisor to create VMs. Next, we outline the requirements to run Minikube on our workstation/laptop:

- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)  
  `kubectl` is a binaryused to access any Kubernetes cluster. Generally, it is installed before starting Minikube, but we can install it later, as well. If `kubectl` is not found while installing Minikube, we will get a warning message, which can be safely ignored (just remember that we will have to install `kubectl` later). We will explore `kubectl` in future chapters.
- On Linux  
  [VirtualBox](https://www.virtualbox.org/wiki/Downloads) or [KVM](https://github.com/kubernetes/minikube/blob/master/docs/drivers.md#kvm-driver) hypervisors
  **NOTE**: Minikube also supports a `--vm-driver=none` option that runs the Kubernetes components on the host and not in a VM. Docker is required to use this driver, but no hypervisor. If you use `--vm-driver=none`, be sure to specify a [bridge network](https://docs.docker.com/network/bridge/#configure-the-default-bridge-network) for Docker. Otherwise, it might change between network restarts, causing loss of connectivity to your cluster.
- On macOS  
  [Hyperkit driver](https://github.com/kubernetes/minikube/blob/master/docs/drivers.md#hyperkit-driver), [xhyve driver](https://github.com/kubernetes/minikube/blob/master/docs/drivers.md#xhyve-driver), [VirtualBox](https://www.virtualbox.org/wiki/Downloads) or [VMware Fusion](http://www.vmware.com/products/fusion.html) hypervisors
- On Windows  
  [VirtualBox](https://www.virtualbox.org/wiki/Downloads) or [Hyper-V](https://github.com/kubernetes/minikube/blob/master/docs/drivers.md#hyperV-driver) hypervisors
- VT-x/AMD-v virtualization must be enabled in BIOS
- Internet connection on first run.

In this chapter, we will use VirtualBox as hypervisor on all three operating systems - Linux, macOS, and Windows, to create the Minikube VM.

## Installing Minikube on Linux

Next, we will learn how to install Minikube on Linux (Ubuntu 16.04):

Install the hypervisor (VirtualBox), if you haven't done so already

`$ sudo apt-get install virtualbox`

**Install Minikube**  
We can download the latest release from the [Minikube release page](https://github.com/kubernetes/minikube/releases). Once downloaded, we need to make it executable and copy it in the PATH:

```
$ curl -Lo \
minikube https://storage.googleapis.com/minikube/releases/v0.25.0/minikube-linux-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/
```

**Start Minikube**  
We can start Minikube with the minikube start command:

```
$ minikube start
Starting local Kubernetes v1.9.0 cluster...
Starting VM...
Downloading Minikube ISO
 142.22 MB / 142.22 MB [============================================] 100.00% 0s
Getting VM IP address...
Moving files into cluster...
Downloading localkube binary
 162.41 MB / 162.41 MB [============================================] 100.00% 0s
 0 B / 65 B [----------------------------------------------------------] 0.00%
 65 B / 65 B [======================================================] 100.00% 0s
Setting up certs...
Connecting to cluster...
Setting up kubeconfig...
Starting cluster components...
Kubectl is now configured to use the cluster.
```

**Check the status**  
With the `minikube status` command, we can see the status of Minikube:

```
$ minikube status
minikube: Running
cluster: Running
kubectl: Correctly Configured: pointing to minikube-vm
at 192.168.99.100
```

**Stop minikube**  
With the `minikube stop` command, we can stop Minikube:

```
$ minikube stop
Stopping local Kubernetes cluster...
Machine stopped.
```

## Installing Minikube on macOS

On macOS, Minikube uses **VirtualBox** as the default hypervisor, which we will use as well. But, we can also use the **xhyve** hypervisor, or the **hyperkit** driver, as well. We can pass the `-vm-driver=<driver>` option while starting the Minikube to use the specific driver.

Next, we will learn how to install Minikube on macOS:

**Install [VirtualBox](http://download.virtualbox.org/virtualbox/5.1.22/VirtualBox-5.1.22-115126-OSX.dmg) on macOS**

**Install Minikube**  
We can download the latest release from the [Minikube release page](https://github.com/kubernetes/minikube/releases). Once downloaded, we need to make it executable and copy it in the PATH.

```
$ curl \
-Lo minikube https://storage.googleapis.com/minikube/releases/v0.25.0/minikube-darwin-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/
```

**Start Minikube**  
We can start Minikube with the `minikube start` command:

```
minikube start
Starting local Kubernetes v1.9.0 cluster...
Starting VM...
Downloading Minikube ISO
 142.22 MB / 142.22 MB [============================================] 100.00% 0s
Getting VM IP address...
Moving files into cluster...
Downloading localkube binary
 162.41 MB / 162.41 MB [============================================] 100.00% 0s
 0 B / 65 B [----------------------------------------------------------] 0.00%
 65 B / 65 B [======================================================] 100.00% 0s
Setting up certs...
Connecting to cluster...
Setting up kubeconfig...
Starting cluster components...
Kubectl is now configured to use the cluster.
Loading cached images from config file.
```

**Check the status**  
We can see the status of Minikube with the `minikube status` command:

```
$ minikube status
minikube: Running
cluster: Running
kubectl: Correctly Configured: pointing to minikube-vm
at 192.168.99.102
```

**Stop Minikube**  
We can stop Minikube with the `minikube stop` command:

```
$ minikube stop
Stopping local Kubernetes cluster...
Machine stopped.
```

## Installing Minikube on Windows

We will be using VirtualBox as the hypervisor to create the Minikube VM. Make sure Hyper-V is disabled while running VirtualBox.

Please note that Windows support is currently in the experimental phase, and you might encounter issues during installation.

Following are the instructions to install Minikube on Windows 10:

Install the latest version of VirtualBox

Go to the Minikube release page

Download the Minikube binary from the Distribution section

Add the downloaded Minikube binary to your PATH

Set the default VM driver for Minikube

Open the Powershell using the Run as Administrator option, and execute the following command:

```
> PS C:\Windows\system32> minikube config set vm-driver virtualbox
These changes will take effect upon a minikube delete and
then a minikube start
```

Start Minikube

We can start Minikube using the `minikube start` command. Open the Powershell using the Run as Administrator option and execute the following command:

```
>PS C:\WINDOWS\system32> minikube start
Starting local Kubernetes v1.9.0 cluster...
Starting VM...
Getting VM IP address
Moving files into cluster...
Downloading localkube binary
 162.41 MB / 162.41 MB [============================================] 100.00% 0s
 0 B / 65 B [----------------------------------------------------------] 0.00%
 65 B / 65 B [======================================================] 100.00% 0s
Setting up certs...
Connecting to cluster...
Setting up kubeconfig...
Starting cluster components...
Kubectl is now configured to use the cluster.
Loading cached images from config file.
```

Check the status

We can see the status of Minikube using the `minikube status` command. Open the Powershell using the Run as Administrator option and execute the following command:

```
> PS C:\WINDOWS\system32> minikube status
minikube: Running
cluster: Running
kubectl: Correctly Configured: pointing to minikube-vm
at 192.168.99.100
```

Stop Minikube

We can stop Minikube using the `minikube stop` command. Open the Powershell using the Run as Administrator option and execute the following command:

```
> PS C:\WINDOWS\system32> minikube stop
Stopping local Kubernetes cluster
Machine stopped.
```

## Minikube CRI-O

According to the [CRI-O website](http://cri-o.io/),

> "CRI-O is an implementation of the Kubernetes CRI (Container Runtime Interface) to enable using OCI (Open Container Initiative) compatible runtimes."

In order to start Minikube with CRI-O, run the following command:

```
$ minikube start --container-runtime=cri-o
Starting local Kubernetes v1.9.0 cluster...
Starting VM...
Getting VM IP address...
Moving files into cluster...
Setting up certs...
Connecting to cluster...
Setting up kubeconfig...
Starting cluster components...
Kubectl is now configured to use the cluster.
Loading cached images from config file.
```

Now, let's do ssh login to the Minikube's VM:

```
$ minikube ssh
$ minikube ssh

                         _             _
            _         _ ( )           ( )
  ___ ___  (_)  ___  (_)| |/')  _   _ | |_      __
/' _ ` _ `\| |/' _ `\| || , <  ( ) ( )| '_`\  /'__`\
| ( ) ( ) || || ( ) || || |\`\ | (_) || |_) )(  ___/
(_) (_) (_)(_)(_) (_)(_)(_) (_)`\___/'(_,__/'`\____)

$
```

**Note**: If you try to list containers using the `docker` command, it will not bring up any results, because we don't use Docker to run containers:

```
$ sudo docker container ls
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
```

To list the containers created via the CRI-O container runtime, use the following command:

```
$ sudo runc list
ID                                                               PID  STATUS        BUNDLE
CREATED                         OWNER
19a91e254e6cb6e6b5677c74a46d6e34b6114389df6032c069d834eff43473a8 3701 running /var/run/containers/storage/overlay-containers/19a91e254e6cb6e6b5677c74a46d6e34b6114389df6032c069d834eff43473a8/userdata 2018-02-13T05:36:58.342206032Z  root 258b88b60665833c6991495b98c0b91b3ebaf5146fd661366fc3c904adaa96b3 3538 running /var/run/containers/storage/overlay-containers/258b88b60665833c6991495b98c0b91b3ebaf5146fd661366fc3c904adaa96b3/userdata 2018-02-13T05:36:34.607314459Z  root 25ddc8d8588b72c1c891644901c92decc58a01b34fe0b303e7654aea029b75a0 4839 running /var/run/containers/storage/overlay-containers/25ddc8d8588b72c1c891644901c92decc58a01b34fe0b303e7654aea029b75a0/userdata 2018-02-13T05:38:03.411396745Z  root 2c0effcb8b7c8afdecfacd3b22b8013c07ab0abf3604466f5f5a59d41c6d7f53 4662 running /var/run/containers/storage/overlay-containers/2c0effcb8b7c8afdecfacd3b22b8013c07ab0abf3604466f5f5a59d41c6d7f53/userdata 2018-02-13T05:37:52.214166848Z  root ...
```

## Learning Objectives (Review)

You should now be able to:

- Discuss Minikube.
- Install Minikube on Linux, Mac, and Windows.
- Verify the installation.
