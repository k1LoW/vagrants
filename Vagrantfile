# -*- mode: ruby -*-
# vi: set ft=ruby :
def install_plugin(plugin)
  system "vagrant plugin install #{plugin}" unless Vagrant.has_plugin? plugin
end

install_plugin('vagrant-vbguest')

Vagrant.configure('2') do |config|
  config.vm.box = ENV['BOX']

  config.vm.box_check_update = true

  config.vm.network 'forwarded_port', guest: 80, host: 8080

  config.vm.synced_folder '.', '/vagrant', disabled: true
  config.vm.synced_folder "#{ENV['HOME']}/src", '/home/vagrant/src'

  config.vm.provider 'virtualbox' do |vb|
    vb.name = 'tmpbox'
    vb.gui = false
    vb.cpus = 2
    vb.memory = '2048'
  end
end
