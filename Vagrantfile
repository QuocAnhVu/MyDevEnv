# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  # Every Vagrant development environment requires a box.
  # This box is pulled from the Vagrant Atlas.
  config.vm.box = "ubuntu/trusty64"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  config.vm.synced_folder "../", "/vagrant"

  config.vm.network "forwarded_port", guest: 3000, host: 3000

  # Use Librarian-Chef to provision Chef cookbooks
  config.librarian_chef.cheffile_dir = "chef"
  # Use Chef solo to provision VM
  config.vm.provision :chef_zero do |chef|
    chef.cookbooks_path = ["chef/cookbooks", "chef/cookbooks_local"]

    chef.json = {
      set_fqdn: "VagrantDev",
      nodejs: {
        npm_packages: [
          { name: "coffee-script" },
          { name: "babel" },
          { name: "browserify" },
          { name: "nodemon" },
          { name: "express-generator" }
        ]
      }
    }

    chef.add_recipe 'hostnames'
    chef.add_recipe 'git'
    chef.add_recipe 'nodejs'
  end
end
