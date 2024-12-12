Vagrant.configure("2") do |config|
  # Debian 12 - ljaaniste-dockerhost
  config.vm.define "ljaaniste-dockerhost" do |dockerhost|
    dockerhost.vm.box = "generic/debian12"
    dockerhost.vm.hostname = "ljaaniste-dockerhost"
    dockerhost.vm.network "public_network", bridge: "Intel(R) Ethernet Connection"
    dockerhost.vm.network "private_network", ip: "10.10.10.130", virtualbox__intnet: "ansible_ljaaniste"
    dockerhost.vm.provider "virtualbox" do |vb|
      vb.name = "ljaaniste-dockerhost"
      vb.memory = "8192"
      vb.cpus = 4
    end
    dockerhost.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y snmpd tmux mc wget tree git
      apt-get install -y docker.io
    SHELL
  end

  # Debian 12 - ljaaniste-ansible
  config.vm.define "ljaaniste-ansible" do |ansible|
    ansible.vm.box = "generic/debian12"
    ansible.vm.hostname = "ljaaniste-ansible"
    ansible.vm.synced_folder "./ansible_data", "/vagrant_data"
    ansible.vm.network "public_network", bridge: "Intel(R) Ethernet Connection"
    ansible.vm.network "private_network", ip: "10.10.10.131", virtualbox__intnet: "ansible_ljaaniste"
    ansible.vm.provider "virtualbox" do |vb|
      vb.name = "ljaaniste-ansible"
      vb.memory = "2048"
      vb.cpus = 2
    end
    ansible.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y snmpd tmux mc wget tree git
      apt-get install -y ansible sshpass yamllint ansible-lint
    SHELL
  end

  # Ubuntu 24.04 - ljaaniste-ubuntu
  config.vm.define "ljaaniste-ubuntu" do |ubuntu|
    ubuntu.vm.box = "generic/ubuntu2204"
    ubuntu.vm.hostname = "ljaaniste-ubuntu"
    ubuntu.vm.network "public_network", bridge: "Intel(R) Ethernet Connection"
    ubuntu.vm.network "private_network", ip: "10.10.10.132", virtualbox__intnet: "ansible_ljaaniste"
    ubuntu.vm.provider "virtualbox" do |vb|
      vb.name = "ljaaniste-ubuntu"
      vb.memory = "2048"
      vb.cpus = 2
    end
    ubuntu.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y snmpd tmux mc wget tree git
    SHELL
  end

  # CentOS Stream 9 - ljaaniste-centos
  config.vm.define "ljaaniste-centos" do |centos|
    centos.vm.box = "centos/stream9"
    centos.vm.hostname = "ljaaniste-centos"
    centos.vm.network "public_network", bridge: "Intel(R) Ethernet Connection"
    centos.vm.network "private_network", ip: "10.10.10.133", virtualbox__intnet: "ansible_ljaaniste"
    centos.vm.provider "virtualbox" do |vb|
      vb.name = "ljaaniste-centos"
      vb.memory = "4096"
      vb.cpus = 2
    end
    centos.vm.provision "shell", inline: <<-SHELL
      dnf update -y
      dnf install -y net-snmp net-snmp-utils tmux mc wget tree git
    SHELL
  end

# OpenSUSE Leap - ljaaniste-opensuse
  config.vm.define "ljaaniste-opensuse" do |opensuse|
    opensuse.vm.box = "opensuse/Leap-15.4.x86_64"
    opensuse.vm.hostname = "ljaaniste-opensuse"
    opensuse.vm.network "public_network", bridge: "Intel(R) Ethernet Connection"
    opensuse.vm.network "private_network", ip: "10.10.10.134", virtualbox__intnet: "ansible_ljaaniste"
    opensuse.vm.provider "virtualbox" do |vb|
      vb.name = "ljaaniste-opensuse"
      vb.memory = "4096"
      vb.cpus = 4
    end
    opensuse.vm.provision "shell", inline: <<-SHELL
      zypper refresh
      zypper update -y
      zypper install -y net-snmp tmux mc wget tree git
    SHELL
  end
end