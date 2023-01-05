# ansible-kubernetes-cluster

Setup and remove a kubernetes cluster with ansible.
Assume that target has Ubuntu 22.04 LTS installed

The YAML files are based on [Deploying a Kubernetes Cluster within Proxmox using Ansible](https://austinsnerdythings.com/2022/04/25/deploying-a-kubernetes-cluster-within-proxmox-using-ansible/) by Austin Pivarnik.

## Modify `ansible-hosts.txt`

```
[all]
192.168.0.50
192.168.0.150
192.168.0.151

[vm_0]
192.168.0.50

[vm_1]
192.168.0.150

[vm_2]
192.168.0.151
```

## Change `ansilbe-vars.yaml` if required

## Setup a cluster

In case installing to every targets listed in `all` section of `ansible-hosts.txt`,
```
ansible-playbook -i ansible-hosts.txt setup-cluster.yaml
```

To specify a node from targets, use `--limit` option

```
ansible-playbook -i ansible-hosts.txt --limit vm_0 -u cychong setup-cluster.yaml
```

## remove the cluster

```
ansible-playbook -i ansible-hosts.txt setup-cluster.yaml
```

or,

```
ansible-playbook -i ansible-hosts.txt --limit vm_0 -u cychong remove-cluster.yaml
```
