# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"

  config.vm.provision "shell", path: "provision_privileged.sh", privileged: true
  
  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.memory = "1024"
  end

  config.vm.define "node1" do |node1|
    node1.vm.provider "virtualbox" do |v|
      v.name = "Elastic Lab Node 1"
    end
    node1.vm.provision "shell", path: "provision_elasticsearch.sh", privileged: false
    node1.vm.network "private_network", ip: "10.0.200.101"
    node1.vm.hostname = "node1"
  end

  # config.vm.define "node2" do |node2|
  #   node2.vm.provider "virtualbox" do |v|
  #     v.name = "Elastic Lab Node 2"
  #   end
  #   node2.vm.provision "shell", path: "provision_elasticsearch.sh", privileged: false
  #   node2.vm.network "private_network", ip: "10.0.200.102"
  #   node2.vm.hostname = "node2"
  # end

  # config.vm.define "node3" do |node3|
  #   node3.vm.provider "virtualbox" do |v|
  #     v.name = "Elastic Lab Node 3"
  #   end
  #   node3.vm.provision "shell", path: "provision_elasticsearch.sh", privileged: false
  #   node3.vm.network "private_network", ip: "10.0.200.103"
  #   node3.vm.hostname = "node3"
  # end

  config.vm.define "node4" do |node4|
    node4.vm.provider "virtualbox" do |v|
      v.name = "Elastic Lab Kibana"
    end
    node4.vm.provision "shell", path: "provision_kibana.sh", privileged: false
    node4.vm.network "private_network", ip: "10.0.200.104"
    node4.vm.hostname = "node4"
  end

end
