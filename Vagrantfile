# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.provider 'virtualbox' do |vb|
    # Customize the amount of memory on the VM:
    vb.memory = 2048
    vb.name = 'odoo'
  end
  config.vm.network 'forwarded_port', guest: 8080, host: 8080
end
