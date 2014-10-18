# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = 'ubuntu/trusty64'

  config.vm.define 'app' do |app|
    app.vm.hostname = 'node-service'
    app.vm.network :private_network, ip: "10.10.1.10"
    app.vm.provision 'ansible' do |ansible|
      ansible.limit = 'all'
      ansible.inventory_path = './inventory'
      ansible.playbook = './service.yml'
    end
  end
end
