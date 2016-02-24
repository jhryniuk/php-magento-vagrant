Vagrant.configure("2") do |conf|
  require 'yaml'
  app_config = YAML.load_file('vars.yml')

  conf.vm.box = "ubuntu/trusty64"

  conf.vm.network :private_network, ip: "10.0.0.200"
  conf.ssh.forward_agent = true

  conf.vm.synced_folder '..', '/var/www/' + app_config["project_name"],
  id: 'vagrant-root', owner: 'vagrant', group: 'vagrant'

  conf.vm.provider :virtualbox do |v|
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--memory", 1024]
    v.customize ["modifyvm", :id, "--name", "magento_" + app_config["project_name"]]
    v.customize ["modifyvm", :id, "--cpuexecutioncap", 80]
    v.cpus = 4
  end

  conf.vm.provision "shell", inline: "
      sudo apt-get --yes install software-properties-common;
      sudo apt-add-repository --yes ppa:ansible/ansible;
      sudo apt-get --yes update ;
      sudo apt-get --yes install ansible
      sudo cp -R /vagrant ~/;
      cd ~/vagrant;
      sudo chmod -x ~/vagrant/provision.yml;
      sudo ansible-playbook ~/vagrant/provision.yml;
      "
end