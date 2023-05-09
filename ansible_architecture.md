## How to connect our controller to our agent nodes

Ansible architecture dictates that the controller (which has ansible installed) connects to the angent nodes. In this case, we have used the Web and Database agent nodes. How we do this? Ansible sends a request to the `host` file to enquire about the agent nodes, and establish a connection between the controller and the agent nodes.
In this way, we can streamline commands to different environments/agent nodes on multiple servers by connecting them to the controller. 

Things to note:
- when prompted for a password use `vagrant`

1. First we ssh into the controller

```
vagrant ssh controller
```

2. We then enter this command which will take us to ansible 

```
cd /etc/ansible
```

3. We SSH into each agent node from the controller using this command 
```
ssh vagrant@<IP address of agent node>
```
4. We then run update and upgrade commands

```
sudo apt update
sudo apt upgrade
```

3. We then exit the two agent nodes (web and db) and we should be back to ansible
4. We then enter the host file

```
sudo nano hosts
```

5. We alter the file by entering our agent nodes IP addresses
```
[web]
192.168.33.10 ansible_connection=ssh ansible_ssh_user=vagrant ansible_ssh_pass=vagrant
[db]
192.168.33.11 ansible_connection=ssh ansible_ssh_user=vagrant ansible_ssh_pass=vagrant

```
6. We then run this command which will `ping` the file and obtain the IP addresses

```
sudo ansible all -m ping
```
7. We should see the following message:

```
192.168.33.11 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    },
    "changed": false,
    "ping": "pong"
}

```

## How to transfer data from the controller to the web server

1. Create a file `testing.txt` and input a line of text

```
sudo nano testing.txt
```
2. Save and exit

```
CTRL + X yes
```
3. Now enter the following command where `src` is the file you would like to move and `dest` is the destination you would move it to 

```
sudo ansible web -m copy -a "src=/etc/ansible/testing.txt dest=/home/vagrant"
```

## Installing nginx using an ansible playbook

![Creating a playbook to install nginx yaml file](https://github.com/fsh-nur/Iac/assets/129324316/d5a92fd7-957c-4eff-9497-0c31184854e9)

## Installing nodejs using an ansible playbook

1. Making sure that you are in the following directory:

```
vagrant@controller:/etc/ansible$
```
2. Create YAML file which we will use to install nodejs

```
sudo nano install-nodejs-playbook.yml
```

3. This will return you to a text file. Following the steps shown in the above diagram we will enter the following(remembering the indents)

```
# YAML file start with ---
---

# where would you like to install nginx
- hosts: web
# would you like to see logs
  gather_facts: yes
# so we need admin access -sudo
  become: true
# add the instructions - commands
  tasks:
  - name: Add node repo
    apt_repository:
      repo: deb https://deb.nodesource.com/node_18.x focal main
      state: present
      filename: nodesource.list
      update_cache: yes
      cache_valid_time: 3600

  - name: Install node.js
    apt:
      name: nodejs
      state:present

  - name: Install npm
      apt:
        name: npm
        state:present

# ensure status is running/active
```
4. This has obtained the nodejs repository and allowed us to install within our playbook
5. Now we run the playbook

```
sudo ansible-playbook install-nodejs-playbook.yml

```
6. 

