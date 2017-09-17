# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

    config.vm.define "main", primary: true do |node|
        node.vm.box = "ubuntu/trusty64"

        node.vm.provision "ansible" do |ansible|
            ansible.playbook = "test.yml"
            ansible.verbose = "vvv"
        end
    end

    config.vm.define "docker" do |node|
        node.vm.box = "williamyeh/ubuntu-trusty64-docker"

        node.vm.provision "shell", inline: <<-SHELL
            cd /vagrant
            docker build  -f test/Dockerfile-ubuntu16.04      -t mysqld_exporter_xenial       .
            docker build  -f test/Dockerfile-ubuntu14.04      -t mysqld_exporter_trusty       .
            docker build  -f test/Dockerfile-ubuntu12.04      -t mysqld_exporter_precise      .
            docker build  -f test/Dockerfile-debian8          -t mysqld_exporter_jessie       .
            docker build  -f test/Dockerfile-debian7          -t mysqld_exporter_wheezy       .
            docker build  -f test/Dockerfile-centos7          -t mysqld_exporter_centos7      .
            docker build  -f test/Dockerfile-centos6          -t mysqld_exporter_centos6      .
        SHELL
    end
end
