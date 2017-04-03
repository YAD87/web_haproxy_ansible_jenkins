# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.box_check_update = false

  config.vm.define "web1" do |web|
      web.vm.network  :private_network, ip: "192.168.34.10", bridge: "eth0"
      web.vm.hostname = "web1"  
      web.vm.provider "virtualbox" do |vb|
         vb.memory = "256"
      end
  end

  
 config.vm.define "web2" do |web2|
     web2.vm.network :private_network, ip: "192.168.34.11", bridge: "eth0"
     web2.vm.hostname = "web2"  
     web2.vm.provider "virtualbox" do |vb|
         vb.memory = "512"
     end
 end

 config.vm.define "haproxy" do |haproxy|
     haproxy.vm.network :private_network, ip: "192.168.34.12", bridge: "eth0"
     haproxy.vm.network :forwarded_port, guest: 80, host: 8000
     haproxy.vm.hostname = "haproxy"
     haproxy.vm.provider "virtualbox" do |vb|
         vb.memory = "256"
     end
 end


 config.vm.define "jenkins" do |ci|
     ci.vm.network :private_network, ip: "192.168.34.13", bridge: "eth0"
     ci.vm.network :forwarded_port, guest: 8080, host: 8080
     ci.vm.hostname = "jenkins"  
     ci.vm.provider "virtualbox" do |vb|
         vb.memory = "1024"
     end
 end


 config.vm.provision "ansible" do |ansible|
    ansible.inventory_path = "ansible2"
    ansible.playbook = "playbook.yml"
    ansible.sudo = true
 end


end
