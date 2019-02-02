# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = 'ubuntu/bionic64'

  config.vm.provider 'virtualbox' do |vb|
    vb.cpus   = 2
    vb.memory = 4096
  end

  config.vm.synced_folder './works', '/home/vagrant/works'
  config.vm.network 'private_network', ip: '192.168.33.10'
  config.vm.network "forwarded_port", guest: 80,   host: 10080
  config.vm.network "forwarded_port", guest: 8080, host: 18080
  config.vm.network "forwarded_port", guest: 443,  host: 10443

  config.vm.provision 'shell', path: './provisioning/init.sh'
  config.vm.provision 'ansible' do |ansible|
    ansible.playbook       = './provisioning/main.yml'
  end
end
