# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/bionic64"

  config.vm.network "private_network", ip: "192.168.63.20"

  config.vm.synced_folder "share", "/share"
  config.vm.synced_folder ".", "/vagrant", disabled: true

  config.vm.provider "virtualbox" do |vb|
    vb.cpus = 4
    vb.memory = "16384" # 16GB
  end

end

