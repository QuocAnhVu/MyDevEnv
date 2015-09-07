# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  # Every Vagrant development environment requires a box.
  config.vm.box = "puppetlabs/ubuntu-14.04-64-puppet"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  config.vm.synced_folder "./", "/vagrant"

  # Workaround for Vagrant using deprecated option 
  # --manifestdir under Puppet 4
  # module_path = "/vagrant/puppet/modules"
  # manifests_path = "/vagrant/puppet/manifests/default.pp"
  # config.vm.provision :shell do |shell|
  #   shell.inline = "/opt/puppetlabs/bin/puppet apply --modulepath=#{module_path} #{manifests_path}"
  # end
  config.vm.provision :puppet do |puppet|
    puppet.manifests_path = "puppet/manifests"
    puppet.module_path = "puppet/modules"
    puppet.options = ['--verbose']
  end
end
