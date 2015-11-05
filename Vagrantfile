# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  ##########
  # Global #
  ##########

  # forward ssh agent
  config.ssh.forward_agent = true

  # mount ~/git
  config.vm.synced_folder "~/git/", "/home/vagrant/git"

  config.vm.provider "virtualbox" do |v|
    # allow symbolic links
    v.customize ["setextradata", :id, "VBoxInternal2/SharedFoldersEnableSymlinksCreate/vagrant", "1"]

    # use the host's resolver as a DNS proxy (fixes slow DNS)
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]

    # be sure that the GUI is disabled
    v.gui = false
  end


  #####################
  # Debian Jessie     #
  #####################
  config.vm.define "jessie" do |jessie|
    jessie.vm.box = "jessie"
    jessie.vm.box_url = "https://github.com/thuetz/vagrant-images/releases/download/v20151017/debian-8.1.0-amd64.box"
    jessie.vm.box_download_checksum_type = "md5"
    jessie.vm.box_download_checksum = "cee9890663794aff22dacfaea90fbfd3"
    jessie.vbguest.auto_update = true
    jessie.vm.network "forwarded_port", guest: 80, host: 10080
    jessie.vm.network "forwarded_port", guest: 443, host: 10443
  end

  #####################
  # Arch Linux        #
  #####################
  config.vm.define "archlinux" do |arch|
    arch.vm.box = "arch"
    arch.vm.box_url = "http://vagrant.srijn.net/archlinux-x64-2014-01-07.box"
    arch.vm.box_download_checksum_type = "sha1"
    arch.vm.box_download_checksum = "cee9890663794aff22dacfaea90fbfd3"
    arch.vbguest.auto_update = true
  end

end
