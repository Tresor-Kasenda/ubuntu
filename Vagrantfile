Vagrant.configure("2") do |config|
  
  config.vm.box = "bento/ubuntu-24.04"
  config.vm.box_architecture = "arm64"

  config.vm.hostname = "learning"

  # Sync folder: host 'script' folder to guest '/scripts/'
	config.vm.synced_folder "scripts", "/opt/scripts"

  config.vm.network "private_network", ip: "192.168.56.10"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = 2048
    vb.cpus = 2
  end

  config.vm.provision "shell", inline: <<-SHELL 
    apt-get update -y
    apt-get install -y nginx
    systemctl enable --now nginx

    mkdir -p /opt/devopsdir
    free -m >> /opt/devopsdir/memory.txt
    df -h >> /opt/devopsdir/disk.txt/opt/devopsdir
  SHELL
end
