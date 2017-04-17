# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  box = ENV['VAGRANT_BOX'] || 'ubuntu/xenial64'
  config.vm.box = box
  config.vm.network 'forwarded_port', guest: 80, host: 8080
  config.vm.provision 'ansible' do |ansible|
    ansible.limit = 'all'
    ansible.inventory_path = 'vagrant'
    # ansible.inventory_path = 'inventory/staging'
    ansible.playbook = "#{ENV['PLAYBOOK'] || 'provision'}.yml"
  end
  config.ssh.forward_agent = true
end
