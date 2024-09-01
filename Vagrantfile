Vagrant.configure("2") do |config|
  config.vm.box = "bento/debian-12"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = 2048
    vb.cpus = 2
  end

  config.vm.define "master" do |node|
    node.vm.hostname = "master"
    node.vm.network "private_network", ip: "192.168.56.10"
    node.vm.network "forwarded_port", guest: 8001, host: 3030, auto_correct: true
    node.vm.network "forwarded_port", guest: 80, host: 8080
    node.vm.network "forwarded_port", guest: 3000, host: 3000
    node.vm.synced_folder ".", "/home/vagrant/shared", disabled: false

    # Provisioning for the master node
    node.vm.provision "shell", name: "disable-swap", path: "scripts/disable-swap.sh", privileged: false
    node.vm.provision "shell", name: "install-essential-tools", path: "scripts/install-essential-tools.sh", privileged: false
    node.vm.provision "shell", name: "allow-bridge-nf-traffic", path: "scripts/allow-bridge-nf-traffic.sh", privileged: false
    node.vm.provision "shell", name: "install-containerd", path: "scripts/install-containerd.sh", privileged: false
    node.vm.provision "shell", name: "install-kubeadm", path: "scripts/install-kubeadm.sh", privileged: false
    node.vm.provision "shell", name: "update-kubelet-config", path: "scripts/update-kubelet-config.sh", args: ["eth1"], privileged: false
  end

  config.vm.define "node1" do |node|
    node.vm.hostname = "node1"
    node.vm.network "private_network", ip: "192.168.56.11"
    node.vm.synced_folder ".", "/home/vagrant/shared"
  end

  config.vm.define "node2" do |node|
    node.vm.hostname = "node2"
    node.vm.network "private_network", ip: "192.168.56.12"
    node.vm.synced_folder ".", "/home/vagrant/shared"
  end
end
