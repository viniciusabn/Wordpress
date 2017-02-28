# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure(2) do |config|
  config.vm.box = "hashicorp/precise32"

  config.vm.define "wordpress" do |wordpress|
    wordpress.vm.network :private_network, ip: "192.168.33.8"
    wordpress.vm.provision "ansible" do |ansible| 
      ansible.playbook = "blog.yml"
      ansible.verbose = "vvv"
    end
  end

  config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--memory", "1024"]
  end
end
