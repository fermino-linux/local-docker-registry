# -*- mode: ruby -*-
# vi: set ft=ruby :

script = "https://raw.githubusercontent.com/fermino-linux/bash-training/main/ansible/install.sh"

Vagrant.configure("2") do |config|

  config.vm.box = "almalinux/8"

  config.vm.network "private_network", ip: "172.16.1.254"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = 1024
    vb.cpus = 1
  end

  config.vm.provision "shell", path: "#{script}", args: "vagrant"
  
  config.vm.provision "ansible_local" do |al|
    al.install = false
    al.galaxy_command = "ansible-galaxy install community.docker"
    al.config_file = "ansible.cfg"
    al.playbook = "playbook.yaml"
  end
end
