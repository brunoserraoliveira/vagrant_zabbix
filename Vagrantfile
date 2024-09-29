Vagrant.configure("2") do |config|

    config.vm.provider "virtualbox" do |vb|
      vb.name = "Zabbix Server"
      vb.memory = 2048
      vb.cpus = 2
    end
  
    # Use uma das versões disponíveis, como "4.0.0"
    config.vm.box = "ubuntu/jammy64"
    config.vm.box_version = "4.0.0"
    
    # Redireciona a porta 80 da VM para a porta 8010 no host
    config.vm.network "forwarded_port", guest: 80, host: 8000
    
    # Configura a rede pública com um IP fixo
    config.vm.network "public_network", ip: "192.168.1.150"
  
    # Executa um script de provisão
    config.vm.provision "shell", path: "script.sh"
  
  end
  