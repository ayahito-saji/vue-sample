# -*- mode: ruby -*-
# vi: set ft=ruby :

$script = <<SHELL
set -i

curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash

source ~/.bashrc

nvm install --lts
nvm alias default lts/*

npm install -g vue-cli

SHELL

Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-16.04"
  config.vm.network "forwarded_port", guest: 3000, host: 3000
  config.vm.network "forwarded_port", guest: 5000, host: 5000
  config.vm.network "forwarded_port", guest: 8080, host: 8080
  config.vm.network "private_network", ip: "192.168.33.10"
  config.vm.provision "shell", privileged: false, inline: $script
end
