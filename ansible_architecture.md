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


