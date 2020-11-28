# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  #config.vm.box = "base"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine and only allow access
  # via 127.0.0.1 to disable public access
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Ansible, Chef, Docker, Puppet and Salt are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL
  config.vm.define "master" do |master|
   master.vm.box = "centos/8"
   master.vm.box_version = "1905.1"
   master.vm.hostname = 'master'
   # network
   master.vm.network :private_network, ip: "10.10.10.100"
   master.vm.network :forwarded_port, guest: 22, host: 10022, id: "guest_ssh"
   master.vm.network :forwarded_port, guest: 80, host: 10080, id: "guest_http"
   
   master.vm.provider :virtualbox do |m|
   m.customize ["modifyvm", :id, "--memory", "1024"]
   m.customize ["modifyvm", :id, "--name", "master"]
   end
  end

  config.vm.define "target1" do |target1|
   target1.vm.box = "centos/8"
   target1.vm.box_version = "1905.1"
   target1.vm.hostname = 'target1'
   # network
   target1.vm.network :private_network, ip: "10.10.10.101"
   target1.vm.network :forwarded_port, guest: 22, host: 10122, id: "guest_ssh"
   target1.vm.network :forwarded_port, guest: 80, host: 10180, id: "guest_http"
   
   target1.vm.provider :virtualbox do |t1|
   t1.customize ["modifyvm", :id, "--memory", "1024"]
   t1.customize ["modifyvm", :id, "--name", "target1"]
   end
  end
  config.vm.define "target2" do |target2|
   target2.vm.box = "centos/8"
   target2.vm.box_version = "1905.1"
   target2.vm.hostname = 'target2'
   # network
   target2.vm.network :private_network, ip: "10.10.10.102"
   target2.vm.network :forwarded_port, guest: 22, host: 10222, id: "guest_ssh"
   target2.vm.network :forwarded_port, guest: 80, host: 10280, id: "guest_http"
   
   target2.vm.provider :virtualbox do |t2|
   t2.customize ["modifyvm", :id, "--memory", "1024"]
   t2.customize ["modifyvm", :id, "--name", "target2"]
   end
  end
end
