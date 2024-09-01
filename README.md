# vagrant-kubernetes-dev-env
# vagrant-kubernetes-dev-env

This repository provides a Vagrant configuration to create a development environment with Debian-based virtual machines. It is specifically designed for setting up a Kubernetes cluster with one master node and two worker nodes.

## Features

- **Master Node**:
  - Hostname: `master`
  - IP Address: `192.168.56.10`
  - Port Forwarding:
    - Guest port 8001 to host port 3030
    - Guest port 80 to host port 8080
    - Guest port 3000 to host port 3000

- **Node1**:
  - Hostname: `node1`
  - IP Address: `192.168.56.11`

- **Node2**:
  - Hostname: `node2`
  - IP Address: `192.168.56.12`

## Provisioning Scripts

The Vagrant configuration uses the following provisioning scripts:

1. **`disable-swap.sh`**: Disables swap memory to improve performance for Kubernetes.
2. **`install-essential-tools.sh`**: Installs necessary tools for the environment.
3. **`allow-bridge-nf-traffic.sh`**: Configures network settings to allow traffic.
4. **`install-containerd.sh`**: Installs containerd, a core component for Kubernetes.
5. **`install-kubeadm.sh`**: Installs kubeadm for Kubernetes cluster management.
6. **`update-kubelet-config.sh`**: Updates kubelet configuration for the specified network interface.

## Requirements

- **Vagrant**: [Download and install Vagrant](https://www.vagrantup.com/downloads).
- **VirtualBox**: [Download and install VirtualBox](https://www.virtualbox.org/wiki/Downloads).

## Getting Started

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yourusername/vagrant-kubernetes-dev-env.git
   cd vagrant-kubernetes-dev-env
