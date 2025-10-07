# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "fedora42"

  # to speed up VM creation disable sync folder
  config.vm.synced_folder ".", "/vagrant", disabled: true

  #config.vm.provider :virtualbox do |v|
    #v.memory = 512
  #end

  # to speed up VM creation, keep insecure ssh key
  config.ssh.insert_key = false

  # Ansible provisioner.
  config.vm.provision :ansible do |ansible|
    ansible.playbook = "main.yml"
#    ansible.skip_tags = ['docker']
#    ansible.tags = ['always', 'docker', 'jellyfin']
#    ansible.tags = ['always', 'dotfiles']
  end

end
