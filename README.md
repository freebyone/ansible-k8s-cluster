# ansible-k8s-cluster
# My Custom Kubespray Repository

This is a custom fork of Kubespray for deploying a Kubernetes cluster on my virtual machines (VMs), with integrations for Argo CD, Calico CNI, dynamic VM discovery, and custom configurations.

## Overview
- **Base**: Forked from [kubernetes-sigs/kubespray](https://github.com/kubernetes-sigs/kubespray).
- **Customizations**:
  - Inventory for my VMs (static or dynamic via discovery script).
  - Argo CD as an addon for GitOps.
  - Calico as the CNI plugin (configurable).
  - All variables and settings in `inventory/my-cluster/group_vars`.
  - Support for secrets via Ansible Vault.

This setup assumes Ubuntu-based VMs, but can be adapted. Minimum requirements: 1 master node + 2 worker nodes for a basic cluster.

## Requirements
- Ansible 9.0+ (install via `pip install -r requirements.txt`).
- Python 3 with dependencies (jq for scripts, etc.).
- SSH access to VMs (keys configured in `~/.ssh/id_rsa` or via inventory).
- VMs prepared: OS installed, firewall ports open (e.g., 6443 for API, 10250 for kubelet), swap disabled (`swapoff -a`), and sufficient resources (at least 2 CPU/4GB RAM per node).
