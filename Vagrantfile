Vagrant.configure("2") do |config|
  # Configuración de la VM
  config.vm.box = "ubuntu/bionic64" # Uso de una distribución Ubuntu
  config.vm.hostname = "apache-server"

  # Configuración de la red (puedes usar privada o puente)
  config.vm.network "private_network", type: "dhcp" # Asignación de una IP dinámica

  # 512 MB de RAM y 1 CPU
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "512"
    vb.cpus = 1
  end

  # Sincronización de la carpeta local con Apache
  config.vm.synced_folder "./paginas_web", "/var/www/html", type: "virtualbox"

  # Redirección de puerto para poder acceder al servidor web desde el navegador
  config.vm.network "forwarded_port", guest: 80, host: 7071

  # Script para instalar Apache en la VM
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y apache2
  SHELL
end
