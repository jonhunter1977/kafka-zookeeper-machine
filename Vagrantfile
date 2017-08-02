# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    # Pick your virtual box image - https://atlas.hashicorp.com/boxes/search - is a good resource
    # config.vm.box = "box-cutter/ubuntu1404-desktop"
    config.vm.box = "ubuntu/trusty64"

    # network config
    config.vm.network "private_network", ip: "192.168.10.4"
    config.vm.hostname = "192.168.10.4"

    # set the name of your vm here
    config.vm.define "kafka-machine" do |d|

    # bug workaround as vagrant seems to have trouble creating synced folder
    config.vm.synced_folder ".", "/vagrant"

    # uncomment/copy the line below if you want to do any port forwarding
    config.vm.network "forwarded_port", guest: 9092, host: 9092
    config.vm.network "forwarded_port", guest: 9093, host: 9093
    config.vm.network "forwarded_port", guest: 2181, host: 2181

    # uncomment/copy the line below if you want to sync any host folders to the guest
    config.vm.synced_folder "./ansible", "/provisioning"
  end

  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--cableconnected1", "on"]

    # use host for internet connectivity
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]

    # Customize the amount of memory on the VM:
    vb.memory = "8192"
  end

  # provision the machine using ansible running on the guest
  # this will install ansible on the guest
  config.vm.provision "ansible_local" do |ansible|
    ansible.inventory_path = "ansible/hosts"
    ansible.playbook = "ansible/playbook.yml"
  end
end
