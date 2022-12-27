
### configuration parameters ###

#Ubuntu 20.04.5 LTS (Focal Fossa)
BOX_BASE = "ubuntu/focal64"


Vagrant.configure("2") do |config|
  config.vm.box = BOX_BASE
  config.vm.define "master" do | w |
  w.vm.hostname = "master"
  w.vm.network "private_network", ip: "192.168.56.13"
  w.vm.provider "virtualbox" do |vb|
    vb.memory = "4096"
    vb.cpus = 2
    vb.name = "master"
  end
  w.vm.provision "setup-hosts", :type => "shell", :path => "k8s-setup-master.sh" do |s|
  end
  w.vm.provision "shell", inline: <<-SHELL
    apt update
    apt install -y git wget vim curl
   SHELL
  end

  config.vm.box = BOX_BASE
  config.vm.define "worker-1" do | w |
      w.vm.hostname = "worker-1"
      w.vm.network "private_network", ip: "192.168.56.14"

      w.vm.provider "virtualbox" do |vb|
        vb.memory = "1024"
        vb.cpus = 1
        vb.name = "worker-1"
      end
      w.vm.provision "setup-hosts", :type => "shell", :path => "k8s-setup-master.sh" do |s|
    end
   w.vm.provision "shell", inline: <<-SHELL
     apt update
     apt install -y git wget vim 
   SHELL
  end 
  config.vm.box = BOX_BASE
  config.vm.define "worker-2" do | w |
      w.vm.hostname = "worker-2"
      w.vm.network "private_network", ip: "192.168.56.15"

      w.vm.provider "virtualbox" do |vb|
        vb.memory = "1024"
        vb.cpus = 1
        vb.name = "worker-2"
      end
        w.vm.provision "setup-hosts", :type => "shell", :path => "k8s-setup-master.sh" do |s|
  end
   w.vm.provision "shell", inline: <<-SHELL
     apt update
     apt install -y git wget vim curl
   SHELL
  end  
end
