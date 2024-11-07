# Vagrant prepare VM

- Ubuntu 2310
- CPU 4
- Ram 8192

## Vagrantfile on Windows Virtualbox
- Virtualbox configuration

``` ruby
# -*- mode: ruby -*-
# vi: set ft=ruby :

$script=<<-SCRIPT
    sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config    
    systemctl restart ssh.service
SCRIPT
Vagrant.configure("2") do |config|

  config.vm.box = "generic/ubuntu2310"

  config.vm.define "node1" do |control|
    control.vm.hostname = "node1"
    control.vm.network "private_network", ip: "192.168.35.10"
    control.vm.provider "virtualbox" do |vb|
      vb.memory = "8192"
      vb.cpus = 4
      vb.customize ["modifyvm", :id, "--nested-hw-virt", "on"]
    end
  end

  config.vm.define "node2" do |control|
    control.vm.hostname = "node2"
    control.vm.network "private_network", ip: "192.168.35.20"
    control.vm.provider "virtualbox" do |vb|
      vb.memory = "8192"
      vb.cpus = 4
      vb.customize ["modifyvm", :id, "--nested-hw-virt", "on"]
    end
  end
  
  config.vm.provision "shell", inline: $script

end
```

Run vagrant up:
```
$ vagrant up --provider=virtualbox
$ vagrant ssh node1
```

## Vagrantfile on Linux KVM
- libvirt configuration

``` ruby
# -*- mode: ruby -*-
# vi: set ft=ruby :

$script=<<-SCRIPT
    sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config    
    systemctl restart ssh.service
SCRIPT
Vagrant.configure("2") do |config|

  config.vm.box = "generic/ubuntu2310"

  config.vm.define "node1" do |control|
    control.vm.hostname = "node1"
    control.vm.network "private_network", ip: "192.168.35.10"
    control.vm.provider "libvirt" do |libvirt|
      libvirt.memory = "8192"
      libvirt.cpus = 4
      libvirt.nested = true
    end
  end

  config.vm.define "node2" do |control|
    control.vm.hostname = "node2"
    control.vm.network "private_network", ip: "192.168.35.20"
    control.vm.provider "libvirt" do |libvirt|
      libvirt.memory = "8192"
      libvirt.cpus = 4
      libvirt.nested = true
    end
  end
  
  config.vm.provision "shell", inline: $script

end
```

Run vagrant up:
```
$ vagrant up --provider=libvirt
$ vagrant ssh node1
```