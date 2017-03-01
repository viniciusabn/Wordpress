# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure(2) do |config|
  config.vm.box = "hashicorp/precise32"

  config.vm.define "db" do |dbvm|
    dbvm.vm.network :private_network, ip: "192.168.33.11"
    dbvm.vm.provision "ansible" do |ansible| 
      ansible.playbook = "blog.yml"
      ansible.verbose = "vvv"
      ansible.groups = {
	"web" => ["192.168.33.10"],
	"db"  => ["192.168.33.11"],
      }
      ansible.limit = "db"
    end
  end

  config.vm.define "web" do |webvm|
    webvm.vm.network :private_network, ip: "192.168.33.10"
    webvm.vm.provision "ansible" do |ansible| 
      ansible.playbook = "blog.yml"
      ansible.verbose = "vvv"
      ansible.groups = {
	"web" => ["192.168.33.10"],
	"db"  => ["192.168.33.11"],
      }
      ansible.limit = "web"
    end
  end

  config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--memory", "1024"]
  end
end
