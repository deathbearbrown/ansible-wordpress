VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"

  # Network configuration.
  config.vm.network :private_network, ip: "192.168.50.20"

  #config.vm.network :forwarded_port, host: 8080, guest: 80

  config.vm.provision :ansible do |ansible|
    ansible.limit = "appserver"
    ansible.inventory_path = "ansible/inventory/vagrant"
    ansible.playbook = "ansible/vagrant.yml"
  end
  config.vm.synced_folder ".", "/vagrant", disabled: true
end
