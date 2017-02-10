# Vagrant configuration version "2" is recommended
Vagrant.configure("2") do |config|

  # Downloads Ubuntu box from https://atlas.hashicorp.com/search
  config.vm.box = "ubuntu/xenial64"
  config.vm.box_check_update = false
  config.ssh.username = "ubuntu"

  # Port forwarding for Alfresco
  config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: "192.168.50.100"

  # Configuration for VirtualBox:
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "4096"
    vb.cpus = 2
  end
  
  # install and run Ansible from within the VM
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "provisioning/playbook.yml"
  end  
  
end
