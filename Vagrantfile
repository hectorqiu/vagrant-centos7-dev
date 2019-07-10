# -*- mode: ruby -*-
# vi: set ft=ruby :


# 检查 Vagrant 插件是否安装

# required_plugins = %w[vagrant-plugin-1 vagrant-plugin-2 vagrant-plugin-3]
required_plugins = %w(vagrant-share vagrant-vbguest vagrant-disksize)

return if !Vagrant.plugins_enabled?

plugins_to_install = required_plugins.select { |plugin| !Vagrant.has_plugin? plugin }

if plugins_to_install.any?
  system "vagrant plugin install #{plugins_to_install.join(' ')}"
  exit system 'vagrant up'
end

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://app.vagrantup.com/boxes/search
  config.vm.box = "centos/7"
  config.vm.hostname = "centos7-dev"
  config.vm.box_check_update = false

  # config.disksize.size = '15GB'  centos7 默认 40G，大于这个取值才需要设置
  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network "forwarded_port", guest: 80, host: 8000
  config.vm.network "forwarded_port", guest: 2333, host: 2333 
  config.vm.network "forwarded_port", guest: 3306, host: 13306  # mysql
  config.vm.network "forwarded_port", guest: 1433, host: 11433  # sql server
  config.vm.network "forwarded_port", guest: 5000, host: 5000
  config.vm.network "forwarded_port", guest: 5100, host: 5100
  config.vm.network "forwarded_port", guest: 5200, host: 5200
  config.vm.network "forwarded_port", guest: 6379, host: 6379   # redis
  config.vm.network "forwarded_port", guest: 8000, host: 8000
  config.vm.network "forwarded_port", guest: 8080, host: 8080
  config.vm.network "forwarded_port", guest: 8888, host: 8888
  config.vm.network "forwarded_port", guest: 27017, host: 27017

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.233.233"
  config.vm.network "private_network", type: "dhcp"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"
  # config.vm.network "public_network", bridge: "en0: Wi-Fi (Wireless)"
  config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"
  # config.vm.synced_folder "/Users/hectorqiu", "/mnt/mac"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  config.vm.provider "virtualbox" do |vb|
      vb.name = "centos7-dev"
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
      vb.memory = "2048"
      vb.cpus = 2
  end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Define a Vagrant Push strategy for pushing to Atlas. Other push strategies
  # such as FTP and Heroku are also available. See the documentation at
  # https://docs.vagrantup.com/v2/push/atlas.html for more information.
  # config.push.define "atlas" do |push|
  #   push.app = "YOUR_ATLAS_USERNAME/YOUR_APPLICATION_NAME"
  # end

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #
    config.vm.provision "shell", inline: "swapoff -a"
    config.vm.provision "shell", inline: "sudo yum install -y epel-release"
    # config.vm.provision "shell", path: "./bootstrap.sh"
  # SHELL
end
