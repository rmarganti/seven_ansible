# -*- mode: ruby -*-
# vi: set ft=ruby :

hostname = "dev"
server_ip = "10.22.2.2"
server_mem = "3072"
server_cpus = 1

Vagrant.configure("2") do |config|
    config.vm.box = "centos/7"
    config.vm.hostname = hostname

    config.vm.network "private_network", ip: server_ip
    config.vm.network :forwarded_port, guest: 3306, host: 3306
    config.vm.network :forwarded_port, guest: 11300, host: 11300

    config.vm.provider :virtualbox do |vb|
        vb.customize ["modifyvm", :id, "--cableconnected1", "on"]
        vb.customize ["modifyvm", :id, "--memory", server_mem]
        vb.cpus = server_cpus
    end

    config.vm.provision "ansible" do |ansible|
        ansible.playbook = "provisioning/playbook.yml"
    end

    config.vm.synced_folder "./", "/vagrant",
        id: "vagrant-root",
        :owner => "vagrant",
        :group => "apache",
        :mount_options => ["dmode=775,fmode=664"]
end
