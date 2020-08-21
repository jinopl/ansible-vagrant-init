# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "geerlingguy/centos7"
  config.ssh.insert_key = false

  config.vm.provider :virtualbox do |v|
    v.name = "ansible-dev"
    v.memory = 256
    v.cpus = 1
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--ioapic", "on"]
  end

  config.vm.hostname = "dev"
  config.vm.network :private_network, ip: "192.168.33.27"

  # Ansible provisioner.
  config.vm.provision "ansible" do |ansible|
    ansible.compatibility_mode = "2.0"
    ansible.playbook = "provision/site.yml"
    ansible.become = true
  end

end