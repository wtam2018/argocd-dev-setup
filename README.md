# Getting argocd dev environment setup using Microk8s local cluster

## Prepare for Microk8s installation (for Fedora 32)

If you are running Fedora 32, you want to disable the following.

* Rollback to CGroups v1
```shell
sudo grubby --update-kernel=ALL --args="systemd.unified_cgroup_hierarchy=0"
```
* disable selinux
Edit /etc/selinux/config to set `SELINUX=disabled`
```shell
sudo sed -i 's/SELINUX=.*/SELINUX=disabled/g' /etc/selinux/config
```

* change default firewall to set FirewallBackend=iptables
Edit /etc/firewalld/firewalld.conf to set `FirewallBackend=iptables`
```shell
sudo sed -i 's/FirewallBackend=.*/FirewallBackend=iptables/g' /etc/firewalld/firewalld.conf
```
* Reboot

## Install Microk8s

Following this steps to install microk8s.
https://snapcraft.io/install/microk8s/fedora

Microsk8s is started after the installation is complete.  You can use `kubectl` to work with your cluster

Here is the documentation on Microk8s using `kubectl`
https://microk8s.io/docs/working-with-kubectl

## Build and run argocd locally

Following this steps to run argocd locally
https://github.com/argoproj/argo-cd/blob/master/docs/developer-guide/running-locally.md#running-argocd-locally

You will probably hit this issue and need this fix/workaround.   https://github.com/argoproj/argo-cd/pull/4210



