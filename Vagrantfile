Vagrant.configure("2") do |config|
    # config.vm.box = "hashicorp/bionic64"
    config.vm.box = "ubuntu/trusty64"

    config.vm.provider "virtualbox" do |virtualbox|
        virtualbox.memory = 1024
        virtualbox.cpus = 2
    end

    config.vm.define "wordpress" do |wordpress|
        wordpress.vm.network "private_network", ip: "192.168.1.101"
        wordpress.vm.provision "shell", inline: 'cat /vagrant/ssh-keys/vagrant_id_rsa.pub >> .ssh/authorized_keys'
        wordpress.vm.provider "virtualbox" do |virtualbox|
            virtualbox.name = "ubuntu_bionic_wordpress"
        end
    end

    config.vm.define "mysql" do |mysql|
        mysql.vm.network "private_network", ip: "192.168.1.102"
        mysql.vm.provision "shell", inline: 'cat /vagrant/ssh-keys/vagrant_id_rsa.pub >> .ssh/authorized_keys'
        mysql.vm.provider "virtualbox" do |virtualbox|
            virtualbox.name = "ubuntu_bionic_mysql"
        end
    end
end 