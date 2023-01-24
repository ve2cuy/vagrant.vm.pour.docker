# -*- mode: ruby -*-
# vi: set ft=ruby :
# ENV['VAGRANT_NO_PARALLEL'] = 'yes'
# --------------------------------------------------------------------
# Fichier:      Vagrantfile
# Version:      1.0
# Auteur:       Alain Boudreault
# Date:         2023.01.24
# Description:  Création d'une VM virtualbox de type Ubuntu srv 20.04,
#               avec installation de docker (docker.io)
#               et des alias pour Docker et K8S
# --------------------------------------------------------------------


Vagrant.configure(2) do |config|

  config.vm.provision "shell", path: "bootstrap.sh"

  NodeCount = 1

  (1..NodeCount).each do |i|

    config.vm.define "ubuntuvm#{i}" do |node|
      # La box est cocumentée ici:
      # https://app.vagrantup.com/bento/boxes/ubuntu-20.04ssh
      node.vm.box               = "bento/ubuntu-20.04"
      node.vm.box_check_update  = false
      #node.vm.box_version       = "3.3"
      node.vm.hostname          = "ubuntuvm#{i}.4204d4.cstj"

      node.vm.network "private_network", ip: "192.168.56.10#{i}"

      node.vm.provider :virtualbox do |v|
        v.name    = "ubuntu-srv#{i}"
        v.memory  = 4048
        v.cpus    = 4
      end

    end

  end

end