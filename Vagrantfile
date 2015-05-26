# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  # Ubuntu 14.04 is capable of running docker without any kernel modifications
  config.vm.box = "ubuntu/trusty64"

  ssh_public_key = File.read(File.join(Dir.home, ".ssh", "id_rsa.pub"))

  config.vm.network "private_network", ip: "192.168.33.100"
  config.vm.hostname = "docker"

  # To make running ansible playbooks against vagrant hosts a smoother experience, we
  # run apt-get udpate and copy our public key to the host.
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    echo "#{ssh_public_key}" >> /home/vagrant/.ssh/authorized_keys
  SHELL

  config.vm.provision :ansible do |ansible|
    ansible.playbook = "install-docker.yml"
    ansible.verbose = "v"
  end
end

