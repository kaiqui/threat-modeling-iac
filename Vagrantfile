Vagrant.configure("2") do |config|
  config.vm.box = "gusztavvargadr/windows-10"
  
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
    vb.cpus = 2
  end

  config.vm.define "windows10-vm"

  #config.vm.synced_folder ".", "/vagrant", type: "virtualbox"

  #config.vm.network "forwarded_port", guest: 80, host: 8080
  #config.vm.network "forwarded_port", guest: 443, host: 8443


  config.vm.provision "shell", inline: <<-SHELL
    $url = "https://download.microsoft.com/download/4/F/D/4FDDEA98-4ABD-47A7-AA0E-815CE8660A76/ThreatModelingTool2016.msi"
    $output = "C:\\Windows\\Temp\\ThreatModelingTool2016.msi"

    Invoke-WebRequest -Uri $url -OutFile $output

    Start-Process -FilePath "msiexec.exe" -ArgumentList "/i", $output, "/quiet", "/norestart" -Wait
  SHELL

end
