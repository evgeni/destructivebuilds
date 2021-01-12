# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define "foreman" do |node|
    node.vm.hostname = "foreman.yatsu.example.com"
    node.vm.box = "centos/7"
    node.vm.synced_folder ".", "/vagrant", disabled: true

    node.vm.provider :libvirt do |libvirt|
      libvirt.memory = 8192
      libvirt.cpus = 4
    end

    node.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbook.yml"
    end
  end

  config.vm.define "client" do |node|
    node.vm.hostname = "client.yatsu.example.com"
    node.vm.box = "centos/7"
    node.vm.synced_folder ".", "/vagrant", disabled: true

    node.vm.provision "ansible" do |ansible|
      ansible.playbook = "client.yml"
    end
  end
end
