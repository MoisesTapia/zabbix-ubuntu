# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "bento/ubuntu-18.04"
  config.vm.hostname="zabbix"
  config.vm.network "public_network"
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update -y
    sudo apt-get install wget -y
    wget https://repo.zabbix.com/zabbix/4.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_4.0-2+bionic_all.deb
    sudo dpkg -i zabbix-release_4.0-2+bionic_all.deb
    sudo apt-get update -y
    sudo apt install zabbix-server-mysql -y
    sudo apt install zabbix-frontend-php -y
    sudo apt install zabbix-agent -y
    sudo service zabbix-agent start
    sudo apt install zabbix-java-gateway -y
    sudo service zabbix-java-gateway restart
    sudo systemctl enable zabbix-java-gateway
  SHELL
end
