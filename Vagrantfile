Vagrant.configure("2") do |config|
  config.hostmanager.enabled = true 
  config.hostmanager.manage_host = true
  config.vbguest.auto_update = false

### Frontend ###
  config.vm.define "jenkins" do |jenkins|
    jenkins.vm.box = "ubuntu/focal64"
    jenkins.vm.hostname = "jenkins"
    jenkins.vm.network "private_network", ip: "192.168.56.133"
    jenkins.vm.synced_folder ".\\vagrant_folder\\", "/vagrant"
    jenkins.vm.provider "virtualbox" do |vb|
      vb.memory = "2000"
      vb.name = "jenkins"
    end
    jenkins.vm.provision "shell", path: ".\\vagrant_folder\\init.sh"
    # docker01.vm.provision "shell", path: ".\\vagrant_folder\\docker.sh"
  end

  config.vm.define "nexus" do |nexus|
    nexus.vm.box = "ubuntu/focal64"
    nexus.vm.hostname = "nexus"
    nexus.vm.network "private_network", ip: "192.168.56.135"
    nexus.vm.synced_folder ".\\vagrant_folder\\", "/vagrant"
    nexus.vm.provider "virtualbox" do |vb|
      vb.memory = "4000"
      vb.name = "nexus"
      vb.cpus = "4"
    end
    nexus.vm.provision "shell", path: ".\\vagrant_folder\\nexus-setup.sh"
    # docker01.vm.provision "shell", path: ".\\vagrant_folder\\docker.sh"
  end
  
  config.vm.define "sonarqube" do |sonarqube|
    sonarqube.vm.box = "ubuntu/focal64"
    sonarqube.vm.hostname = "sonarqube"
    sonarqube.vm.network "private_network", ip: "192.168.56.140"
    sonarqube.vm.synced_folder ".\\vagrant_folder\\", "/vagrant"
    sonarqube.vm.provider "virtualbox" do |vb|
      vb.memory = "4000"
      vb.name = "sonarqube"
    end
    sonarqube.vm.provision "shell", path: ".\\vagrant_folder\\sonar-setup.sh"
  end
end