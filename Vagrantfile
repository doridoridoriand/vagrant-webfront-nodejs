
# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = 'ubuntu/trusty64'

  config.vm.provider 'virtualbox' do |vb|
    vb.cpus   = 2
    vb.memory = 2048
  end

  config.vm.synced_folder './works', '/home/vagrant/works'
  config.vm.network 'private_network', ip: '192.168.33.10'

  config.vm.provision 'ansible' do |ans|
    ans.playbook       = 'provisioning/webfront.yml'
    ans.inventory_path = 'provisioning/hosts'
    ans.limit          = 'all'
  end
end
