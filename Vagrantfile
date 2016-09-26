# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.define "desktop" do |desk|
    desk.vm.box = "boxcutter/centos72-desktop"
    desk.vm.hostname = "samba"
  #Workaround for Vagrant v1.8.5 bug
  #https://github.com/mitchellh/vagrant/issues/7610
  config.ssh.insert_key = false
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provision/ansible/playbook-samba-shares.yml"
    desk.vm.provider "virtualbox" do |v|
      v.gui = true
      v.customize ["modifyvm", :id, "--memory", 4096]
      v.customize ["modifyvm", :id, "--cpus", 4]
      v.customize ["modifyvm", :id, "--vram", "256"]
      v.customize ["setextradata", "global", "GUI/MaxGuestResolution", "any"]
      v.customize ["setextradata", :id, "CustomVideoMode1", "1920x1080x32"]
      v.customize ["modifyvm", :id, "--ioapic", "on"]
      v.customize ["modifyvm", :id, "--rtcuseutc", "on"]
      v.customize ["modifyvm", :id, "--accelerate3d", "on"]
      v.customize ["modifyvm", :id, "--clipboard", "bidirectional"]
    end
  end
end
end
