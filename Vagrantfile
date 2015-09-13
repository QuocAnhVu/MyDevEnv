# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  # Every Vagrant development environment requires a box.
  # This box is pulled from the Vagrant Atlas.
  config.vm.box = "debian/jessie64"

  # Share a folder to the guest VM.
  config.vm.synced_folder "../", "/vagrant"

  forwadedPorts = [3000, 4444, 80, 8080]
  forwadedPorts.each { |port| config.vm.network "forwarded_port", guest: port, host: port }

  # Enables symlink creation within vm on Windows hosts
  # config.vm.provider "virtualbox" do |v|
  #     v.customize ["setextradata", :id, "VBoxInternal2/SharedFoldersEnableSymlinksCreate/vagrant", "1"]
  # end

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
          { name: "express-generator" },
          { name: "jade" },
          { name: "sails" }
        ]
      },
      homerc: {
        users: ['vagrant']
      }
    }

    recipes = ['hostnames', 'git', 'nodejs', 'vim', 'homerc']
    recipes.each { |recipe| chef.add_recipe recipe }
  end
end
