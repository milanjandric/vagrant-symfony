# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.require_version ">= 1.5"

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "https://oss-binaries.phusionpassenger.com/vagrant/boxes/latest/ubuntu-14.04-amd64-vbox.box"
  config.vm.network :private_network, ip: "33.33.33.15"
  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", 2048]
    vb.customize ["modifyvm", :id, "--cpus", 1]
    vb.customize ["guestproperty", "set", :id, "--timesync-set-threshold", "15000"]
  end
  config.vm.synced_folder "./project", "/vagrant", id: "vagrant-root", :nfs => true
  config.vm.provision :ansible do |ansible|
      ansible.playbook = "provision/vagrant.yml"
      ansible.inventory_path = "provision/inventory/vagrant"
      ansible.verbose = 'v'
      ansible.host_key_checking = false
      ansible.limit = 'all'
    end
end
