
Vagrant.configure("2") do |config|
  config.vm.box = "gusztavvargadr/windows-server"

  #switch off updates checking
  config.vm.box_check_update = false

  #forwarding port
  config.vm.network "forwarded_port", guest: 80, host: 8080

  #provide more resources for VM
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
    vb.cpus = 2
  end

  #enable standard vagrant/vm windows communicator
  config.vm.communicator = "winrm"

  #install IIS services
  config.vm.provision :shell, path: 'install-iis.ps1'

  #copy the index.html file to a IIS www folder
  config.vm.provision 'file', source: 'index.html', destination: 'C:/inetpub/wwwroot/'
end
