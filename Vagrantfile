# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = 'ubuntu/trusty64'

  config.vm.define 'service' do |service|
    service.vm.hostname = 'node-service'
    service.vm.network :private_network, ip: "10.10.1.10"
    service.vm.provision 'ansible' do |ansible|
      ansible.limit = 'all'
      ansible.inventory_path = './inventory'
      ansible.playbook = './service.yml'
    end
  end

  config.vm.define 'redis' do |redis|
    redis.vm.hostname = 'redis'
    redis.vm.network :private_network, ip: "10.10.1.11"
    redis.vm.provision 'ansible' do |ansible|
      ansible.limit = 'all'
      ansible.inventory_path = './inventory'
      ansible.playbook = './redis.yml'
    end
  end

end
