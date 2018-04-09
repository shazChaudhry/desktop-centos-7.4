# -*- mode: ruby -*-
# vi: set ft=ruby :

$docker_swarm_init = <<SCRIPT
echo "============== Initializing swarm mode ====================="
docker swarm init --advertise-addr 192.168.99.101 --listen-addr 192.168.99.101:2377
SCRIPT

Vagrant.configure("2") do |config|

  config.vm.box = "joemann/centos7-vbox-gnome"
  config.hostmanager.enabled = true
	config.hostmanager.manage_host = true
	config.hostmanager.manage_guest = true
	# config.vm.provision "docker"

  config.vm.define "node1", primary: true do |node1|
    node1.vm.hostname = 'node1'
    node1.vm.network :private_network, ip: "192.168.99.101"
    node1.vm.provider :virtualbox do |v|
      v.gui = true
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--memory", 8000]
      v.customize ["modifyvm", :id, "--name", "node1"]
    end
    # node1.vm.provision :shell, inline: $docker_swarm_init
    node1.vm.provision "file", source: "~/.ssh", destination: "$HOME/.ssh"
    node1.vm.provision "shell", inline: "chmod 600 /home/vagrant/.ssh/*"
    node1.vm.provision "file", source: "~/.aws", destination: "$HOME/.aws"
    node1.vm.provision "shell", inline: "chmod 600 /home/vagrant/.aws/*"
    # node1.vm.provision "shell", inline: "gsettings set org.gnome.nautilus.icon-view default-zoom-level small"
    node1.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "ansible/site.yml"
    end
  end

end
