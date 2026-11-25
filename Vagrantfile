# -*- mode: ruby -*-
# vim: set ft=ruby :

# Указываем зеркало для скачивания образов
ENV['VAGRANT_SERVER_URL'] = 'https://vagrant.elab.pro'

Vagrant.configure("2") do |config|

# 1. ipa.otus.lan * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * 
  config.vm.define "ipa" do |ipa|
    ipa.vm.box = "almalinux/9"
    ipa.vm.hostname = "ipa.otus.lan"
    ipa.vm.provider "virtualbox" do |v|
      v.memory = 2048
      v.cpus = 2
    end

    ipa.vm.network "private_network", ip: "192.168.57.10", adapter: 2, netmask: "255.255.255.0", virtualbox__intnet: "ldap-net"

    ipa.vm.provision "shell",
      run: "always",
      inline: <<-SHELL
        sudo nmcli con reload
        sudo nmcli con up 'System eth1'
      SHELL
  end

  # 2. client1.otus.lan * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * 
    config.vm.define "client1" do |client1|
    client1.vm.box = "almalinux/9"
    client1.vm.hostname = "client1.otus.lan"
    client1.vm.provider "virtualbox" do |v|
      v.memory = 2048
      v.cpus = 2
    end

    client1.vm.network "private_network", ip: "192.168.57.11", adapter: 2, netmask: "255.255.255.0", virtualbox__intnet: "ldap-net"

    client1.vm.provision "shell",
      run: "always",
      inline: <<-SHELL
        sudo nmcli con reload
        sudo nmcli con up 'System eth1'
      SHELL
  end

# 3. client2.otus.lan * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * 
  config.vm.define "client2" do |client2|
    client2.vm.box = "almalinux/9"
    client2.vm.hostname = "client2.otus.lan"
    client2.vm.provider "virtualbox" do |v|
      v.memory = 2048
      v.cpus = 2
    end

    client2.vm.network "private_network", ip: "192.168.57.12", adapter: 2, netmask: "255.255.255.0", virtualbox__intnet: "ldap-net"

    client2.vm.provision "shell",
      run: "always",
      inline: <<-SHELL
        sudo nmcli con reload
        sudo nmcli con up 'System eth1'
      SHELL
  end

end
