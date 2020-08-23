# -*- mode: ruby -*-
# vi: set ft=ruby :

ENV["LC_ALL"] = "es_ES.UTF-8"

BOX  = 'ubuntu/xenial64'

Vagrant.configure(2) do |config|

    config.vm.define "dev" do |dev|
        dev.vm.box = BOX
        dev.vm.hostname="dev"
        dev.vm.network :private_network, ip: "192.168.33.139"
        dev.vm.provider "virtualbox" do |vb|
            vb.name = "Dev"             
        end
    end

    # Creamos la máquina test
    config.vm.define "test" do |test|
        test.vm.box = BOX
        test.vm.hostname="test"
        test.vm.network :private_network, ip: "192.168.33.140"                
        test.vm.provider "virtualbox" do |vb|
            vb.name = "Test"             
        end
    end

    # Configuración         
    config.ssh.forward_agent= true
    config.vm.synced_folder ".", "/vagrant", disabled: true    

    # Provisions
  	config.vm.provision 'shell', inline: 'sudo locale-gen es_ES.UTF-8', privileged: true
  	config.vm.provision 'docker'
    config.vm.provision 'docker_compose'
      
    # VirtualBox
    config.vm.provider "virtualbox" do |vb|
        vb.memory = 1024
        vb.cpus = 1        
    end

    # Ansible
    config.vm.provision "ansible" do |ansible|
        ansible.compatibility_mode = "2.0"
        ansible.playbook = "playbook.yml"
        ansible.inventory_path = "provision/inventory"
        ansible.become = true
    end
end