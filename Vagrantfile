# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-16.04"

  config.vm.provider "virtualbox" do |vb|
    # Customize the amount of memory on the VM:
    vb.memory = "1024"
  end

  # Disable the new default behavior introduced in Vagrant 1.7, to
  # ensure that all Vagrant machines will use the same SSH key pair.
  # See https://github.com/mitchellh/vagrant/issues/5005
  config.ssh.insert_key = false
  
  # expose redis to the host machine
  config.vm.network "forwarded_port", guest: 6379, host: 6379, protocol: "tcp"

  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "playbook.yml"
    # enable access from the host machine - DEVELOPMENT ONLY
    # on a web server this would expose redis to the world
    ansible.extra_vars = {
      bind_addr: "0.0.0.0"
    }
  end
end
