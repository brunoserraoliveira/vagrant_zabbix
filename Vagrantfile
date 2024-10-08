# [Provisionamento da MV para a instalação Zabbix]

  Vagrant.configure("2") do |config|
  
    # Box definida: Ubuntu 22.04 (Jammy)
    config.vm.box = "ubuntu/jammy64"
    
    # Definir a quantidade de memória RAM, CPUs e nome da MV
    config.vm.provider "virtualbox" do |vb|
      vb.name = "zabbix-server"
      vb.memory = "2048"
      vb.cpus = 2
    end
    
    # Definir o nome da VM
    config.vm.hostname = "zabbix-server"
  
    # Definir o redirecionamento de porta para usar o IP do host.
    # config.vm.network "forwarded_port", guest: 80, host: 8000

    # Static IP
    config.vm.network "public_network", ip: "192.168.1.50"

  
  # Configurar as variáveis de ambiente e o fuso horário
  config.vm.provision "shell", inline: <<-SHELL
    # Instalar pacotes de idiomas
    sudo apt-get install -y language-pack-pt
    
    # Gerar locales
    locale-gen pt_BR.UTF-8
    update-locale LANG=pt_BR.UTF-8 LANGUAGE=pt_BR:pt:en LC_ALL=pt_BR.UTF-8

    # Definir o fuso horário
    echo 'America/Sao_Paulo' > /etc/timezone
    ln -snf /usr/share/zoneinfo/America/Sao_Paulo /etc/localtime
  SHELL

    # Executar o script externo no provisionamento
    config.vm.provision "shell", path: "script.sh"
  end


 