# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.box = "Kali"
  config.vm.box = "kalilinux/rolling"
  config.vm.host_name = "bardo"
  
  # Customize the amount of space disk (100G)
  # Need plugin :  vagrant plugin install vagrant-disksize
  config.disksize.size = '100GB'

  config.vm.network "private_network", ip: "192.168.33.10"

  config.vm.provider "virtualbox" do |vb|
    # Display the VirtualBox GUI when booting the machine
    vb.gui = true
    # Give name to virtualbox machine
    vb.name = 'Kali'
    # Customize the amount of memory on the VM:
    vb.memory = "10000"
    # Customize the amount of CPUs on the VM:
    vb.cpus = 6
  end

  # TODO config swap
  #config.vm.provision "shell", inline: "/bin/dd if=/dev/zero of=/var/swap.1 bs=1M count=4096d ", run: "always"
  #config.vm.provision "shell", inline: "/sbin/mkswap /var/swap.1", run: "always"
  #config.vm.provision "shell", inline: "/sbin/swapon /var/swap.1", run: "always"

  config.vm.provision "shell", inline: <<-SHELL
    apt-get update -y
    # Configure French keyboard layout
    sed -ie '/^XKBLAYOUT=/s/".*"/"fr"/' /etc/default/keyboard && udevadm trigger --subsystem-match=input --action=change
    # Set up user 
    useradd -m bardo
    PASSWORD=#{ENV['PASSWORD']}
    echo "bardo:$PASSWORD" | sudo chpasswd
    usermod -aG sudo bardo
    # change /bin/sh to /usr/bin/zsh for our new user
    sed -i 's#/bin/sh$#/usr/bin/zsh#' /etc/passwd
    # Install kali necessary tools
    apt install seclists -y
    apt install wpscan -y
    apt install tldr -y
    # Cutter for reverse
    apt install radare2-cutter -y
    # Set password back to nothing
    PASSWORD=''
  SHELL
end
