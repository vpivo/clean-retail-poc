# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "trusty64"
  config.vm.box_url = "https://vagrantcloud.com/ubuntu/boxes/trusty64/versions/14.04/providers/virtualbox.box"

  config.vm.define "elasticsearch" do |machine|
    machine.vm.network "forwarded_port", guest: 80, host: 8081
    machine.vm.network "forwarded_port", guest: 9200, host: 9200
    
    machine.vm.provision :ansible do |ansible|
      ansible.playbook = "infra/ansible/vagrant_elasticsearch_playbook.yml"
    end
  end

  config.vm.define "solr" do |machine|
    machine.vm.network "forwarded_port", guest: 8080, host: 8080
    
    machine.vm.provision :ansible do |ansible|
      ansible.playbook = "infra/ansible/vagrant_solr_playbook.yml"
    end
  end
end
