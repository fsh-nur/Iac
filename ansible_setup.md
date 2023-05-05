## How to set up Ansible using Vagrant

1. Create a vagrant file within a folder using this command:

```
vagrant init
```

2. Input the following code in order to configure the virtual machines of db, web and controller within a vagrant file:

```
# -*- mode: ruby -*-
# vi: set ft=ruby :
# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# MULTI SERVER/VMs environment 
#
Vagrant.configure("2") do |config|
  # creating are Ansible controller
     config.vm.define "controller" do |controller|
       
      controller.vm.box = "bento/ubuntu-18.04"
      
      controller.vm.hostname = 'controller'
      
      controller.vm.network :private_network, ip: "192.168.33.12"
      
      # config.hostsupdater.aliases = ["development.controller"] 
      
     end 
  # creating first VM called web  
     config.vm.define "web" do |web|
       
       web.vm.box = "bento/ubuntu-18.04"
      # downloading ubuntu 18.04 image
       web.vm.hostname = 'web'
       # assigning host name to the VM
       
       web.vm.network :private_network, ip: "192.168.33.10"
       #   assigning private IP
       
       #config.hostsupdater.aliases = ["development.web"]
       # creating a link called development.web so we can access web page with this link instread of an IP   
           
     end
     
  # creating second VM called db
     config.vm.define "db" do |db|
       
       db.vm.box = "bento/ubuntu-18.04"
       
       db.vm.hostname = 'db'
       
       db.vm.network :private_network, ip: "192.168.33.11"
       
       #config.hostsupdater.aliases = ["development.db"]     
     end
  
  end
```

3. SSH into the different virtual machines and update and upgrade each

```
vagrant ssh <vm name>
sudo apt update
sudo apt upgrade -y
```

4. Now once we ssh into the controller VM, this is where we will install ansible:

```
sudo apt install software-properties-common
sudo apt-add-repository ppa:ansible/ansible
sudo apt update -y
sudo apt install ansible
```

5. Now ssh into Vagrant IP using the following code and enter the password `vagrant`:

```
ssh vagrant@192.168.33.10
```

6. 
