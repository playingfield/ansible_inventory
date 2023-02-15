# -*- mode: ruby -*-
# vi: set ft=ruby :

## Use this file if you have VirtualBox and Vagrant installed

Vagrant.configure("2") do |config|
  config.vagrant.plugins = ["vagrant-hostmanager"]

  # Vagrant virtual machines require a box to build off of.
  config.vm.box = "centos/stream8"

  # Use the default insecure key for these machines
  config.ssh.insert_key = false
  # Forward ssh-agent for cloning from Github.com
  config.ssh.forward_agent = true

  # disable updating guest additions
  if Vagrant.has_plugin?("vagrant-vbguest")
    config.vbguest.auto_update = false
  end
  # disable guest additions
  config.vm.synced_folder '.', '/vagrant', disabled: true

  # manage /etc/hosts
  config.hostmanager.enabled = true
  config.hostmanager.include_offline = true
  config.hostmanager.manage_guest = true
  config.hostmanager.manage_host = true


  config.vm.define 'db1' do |db1|
    # Create a private network, which allows host-only access to the machine
    # using a specific IP.
    db1.vm.network "private_network", ip: "192.168.56.21"
    db1.vm.network "forwarded_port", guest: 5432, host: 5432
    db1.vm.hostname = "ansible01"
    db1.vm.provider "virtualbox" do |vb|
      vb.name = "ansible01"
      # Use VBoxManage to customize the VM. For example to change memory:
      vb.customize ["modifyvm", :id, "--memory", "2048"]
    end
  end

  config.vm.define 'db2' do |db2|
    # Create a private network, which allows host-only access to the machine
    # using a specific IP.
    db2.vm.network "private_network", ip: "192.168.56.22"
    db2.vm.hostname = "ansible02"
    db2.vm.provider "virtualbox" do |vb|
      vb.name = "ansible02"
      # Use VBoxManage to customize the VM. For example to change memory:
      vb.customize ["modifyvm", :id, "--memory", "2048"]
    end
  end

  config.vm.define 'db3' do |db3|
    # Create a private network, which allows host-only access to the machine
    # using a specific IP.
    db3.vm.network "private_network", ip: "192.168.56.23"
    db3.vm.hostname = "ansible03"
    db3.vm.provider "virtualbox" do |vb|
      vb.name = "ansible03"
      # Use VBoxManage to customize the VM. For example to change memory:
      vb.customize ["modifyvm", :id, "--memory", "2048"]
    end
  end

  config.vm.define 'web' do |web|
    # Create a private network, which allows host-only access to the machine
    # using a specific IP.
    web.vm.network "private_network", ip: "192.168.56.24"
    web.vm.network "forwarded_port", guest: 80, host: 8000
    web.vm.hostname = "ansible04"
    web.vm.provider "virtualbox" do |vb|
      vb.name = "ansible04"
      # Use VBoxManage to customize the VM. For example to change memory:
      vb.customize ["modifyvm", :id, "--memory", "1024"]
    end

  end

end
