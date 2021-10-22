# Creation of a simple Kubernetes cluster with Ansible

The create-k8s-basic directory contains an ansible playbook (k8s_create.yaml) that may be used to create a simple 3-node kubernetes cluster using the latest stable version of kubernetes and the containerd runtime. Based on the Ansible Playbook created by [CyberGavin](https://github.com/cybergavin). The original repo can be found here: [https://github.com/cybergavin/kubernetes](https://github.com/cybergavin/kubernetes)

## Pre-Requisites
- Three pre-provisioned RHEL 8 nodes with connectivity to the Internet to download packages and images from repositories and registries.
- A user account (srv-admin in my playbook) with sudo (root) privileges provisioned on the ansible control node and all RHEL 8 nodes. Also ensure that the user’s SSH keys are set up to allow execution of the ansible playbook.

## Implementation
- Set the following values in /vars/main.yaml:
  - `pod_network` This is the network to use for your pods
  - `service_network` This is the network to use for services
  - `control_plane_endpoint` This is the URL for your cluster
  - `k8s_version` The version of Kubernetes to install
- Add details for the pre-provisioned RHEL 8 nodes to the files/inventory
- Execute the following command:

      ansible-playbook -i files/inventory k8s_create.yaml -e 'ansible_become_pass=PASS=GOES-HERE'

