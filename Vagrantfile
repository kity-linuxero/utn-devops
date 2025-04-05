# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/jammy64"

  config.vm.network "forwarded_port", guest: 8080, host: 8080

  # Puerto Jenkins
  config.vm.network "forwarded_port", guest: 8082, host: 8082, auto_correct: true

  # Puerto en que escuchar el servidor maestro de Puppet
  config.vm.network "forwarded_port", guest: 8140, host: 8140, auto_correct: true
  
  #Permite descargas con certificados vencidos o por http
  config.vm.box_download_insecure = true

  # configuración del nombre de maquina
  config.vm.hostname = "utn-devops.localhost"
  config.vm.boot_timeout = 3600

  
  config.vm.provider "virtualbox" do |vb|
      vb.name = "utn-devops-vagrant-ubuntu"

    # Customize the amount of memory on the VM:
    vb.memory = "1024"
  end

  # Mapeo de directorios que se comparten entre la maquina virtual y nuestro equipo. En este caso es
  # el propio directorio donde está el archivo  y el directorio "/vagrant" dentro de la maquina virtual.
  # config.vm.synced_folder ".", "/vagrant"

  # Con esta sentencia lo que hara Vagrant es copiar el archivo a la máquina Ubuntu.
  # Además de usarlo como ejemplo para distinguir dos maneras de aprovisionamiento el archivo contiene
  # una definición del firewall de Ubuntu para permitir el tráfico de red que se redirecciona internamente.
  config.vm.provision "file", source: "hostConfigs/ufw", destination: "/tmp/utw"
  config.vm.provision "file", source: "hostConfigs/etc_hosts.txt", destination: "/tmp/etc_hosts.txt"
  
  # Archivos de Puppet
  config.vm.provision "file", source: "hostConfigs/puppet/site.pp", destination: "/tmp/site.pp"
  config.vm.provision "file", source: "hostConfigs/puppet/init.pp", destination: "/tmp/init.pp"
  config.vm.provision "file", source: "hostConfigs/puppet/init_jenkins.pp", destination: "/tmp/init_jenkins.pp"
  config.vm.provision "file", source: "hostConfigs/puppet/puppet-master.conf", destination: "/tmp/puppet-master.conf"
  config.vm.provision "file", source: "hostConfigs/puppet/.env", destination: "/tmp/env"

  # En este archivo tendremos el provisionamiento de software necesario para nuestra
  # maquina virtual. Por ejemplo, servidor web, servidor de base de datos, etc.
  config.vm.provision :shell, path: "Vagrant.bootstrap.sh", run: "always"


end
