# rpi-poc

This repository contains some simple ansible roles to install a few basic components for my personal raspberry pi 4 cluster.

In addition to the roles included in this repository I also deployed :
 
* ansible-k3s (https://github.com/k3s-io/k3s-ansible)

For the workstation node we are using raspian, for the rest of the nodes we switch to ubuntu 22.04
Using ansible-k3s (https://github.com/k3s-io/k3s-ansible) it was necessary to further install following package(s) on the nodes to be able to load the flannel driver :

```
sudo apt install linux-modules-extra-raspi
```

To get a nice interface to interact with our kubernetes cluster we are using k9s from the workstation : 

```
sudo apt update
sudo apt install snapd

sudo reboot
sudo snap install-core
sudo snap install k9s
```

Cephadm ansible (https://github.com/ceph/cephadm-ansible)
Since now there is no jammy release file for quincy, thus we have to workaround a bit

```
ansible -i rpi.hosts all -m "shell" -a "sudo apt install ceph-common"
```
