# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

    config.vm.box = "debian/jessie64"
    config.vm.box_url = "https://github.com/holms/vagrant-jessie-box/releases/download/Jessie-v0.1/Debian-jessie-amd64-netboot.box"
    config.vm.network :private_network, ip: "192.168.34.20"
    config.ssh.forward_agent = true
    config.vm.hostname = "dev-local"
    config.ssh.insert_key = false

    config.vm.provider "virtualbox" do |v|
        v.memory = 4096
        v.cpus = 4 # 8
    end

    config.vm.synced_folder "~/development/personal_projects/urjobhub/jhub_rest", "/var/www/urjobhub",
    owner: "www-data", group: "www-data"
    config.vm.synced_folder "~/development/personal_projects/urjobhub/jhub_ui/tomcat/webapps", "/etc/tomcat8/webapps",
    create: true

#     config.vm.network "forwarded_port", guest: 80, host: 8080

    config.vm.provision :ansible do |ansible|
        ansible.verbose = "v"
        ansible.playbook = "playbook.yml"
        ansible.galaxy_role_file = "requirements.yml"
    end

end
