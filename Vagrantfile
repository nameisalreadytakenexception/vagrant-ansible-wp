Vagrant.configure("2") do |config|
  config.vm.box = "bento/centos-7.8" #"bento/ubuntu-18.04"
  config.vm.define "wordpress"
  config.vm.synced_folder "provisioning", "/vagrant"
  config.vm.provider :virtualbox do |vb|
    vb.memory = "2048"
    vb.cpus = "2"
  end
  
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "wordpress/playbook.yml"
    ansible.galaxy_roles_path = "wordpress/roles"
    ansible.limit = "all"
  end
  
  config.vm.network :forwarded_port, guest: 80, host: 8080
  config.vm.network :private_network, ip: "" ##your host ip!!
  end