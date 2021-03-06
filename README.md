![CentOS 7 desktop screenshot](./images/centos7-desktop.JPG)


`vagrant up` will spin up a CentOS 7.4 desktop VM. This VM is a single node docker swarm mode cluster

_(Optional)_ You will need to ensure that you have an SSH key pair available in ~/.ssh directory. This directory will be coppied to the guest VM

_(Optional)_ You will need to ensure that you have ~/.aws/credentials file available on the host machine. ~/.aws directory will be coppied to the guest VM

The infrastructure created with Vagrantfile will have the following tools installed:
  - Openjdk 1.8.0
  - Maven 3.6.0
  - Git _(latest compatible version)_
  - Ansible _(latest compatible version)_
  - Atom _(latest Beta)_ along with numerous plugins. See "ansible/roles/install-atom-packages/vars/main.yml"
  - Google Chrome _(latest compatible version)_
  - Terraform v0.11.11
  - Docker CE _(latest compatible version)_
