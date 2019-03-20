# Ansible
Ansible works by configuring client machines from an computer with Ansible components installed and configured. It communicates over normal SSH channels and for this reason Ansible does not require any additional software.

##Installation
Ansible needs to be installed on the server side.

1. sudo apt -y install ssh
2. sudo apt-add-repository ppa:ansible/ansible
3. sudo apt update
4. sudo apt -y install ansible

##SSH key setup
As already mentioned above, Ansible primarily communicates with client computers through SSH. While it certainly has the ability to handle password-based SSH authentication, SSH keys help keep things simple.

We will create SSH key pairs on our client. To create a SSH key pair just type `ssh-keygen` in your terminal.

You will be asked to specify the file location of the created key pair, a passphrase, and the passphrase confirmation. Press ENTER through all of these to accept the default values. Your new keys are available in your user's `~/.ssh` directory. The public key (the one you can share) is called **id_rsa.pub**. The private key (the one that you keep secure) is called **id_rsa**.

To see your public key you can use the following command `cat ~/.ssh/id_rsa.pub`. Copy the public keys of the nodes to the server on which Ansible is deployed. To this use the following command.

`ssh-copy-id username@nodeip `

##Confguring Ansible

Ansible keeps track of all of the nodes that it knows about through a "hosts" file. We need to set up this file first before we can begin to communicate with our other computers. We need to add the node IP address in the configuration file.

Add the following line in the **hosts** file.


`[test]`
`host1 ansible_ssh_host=nodeIP`


##Check setup

To check the connection between Ansible node and server.

`ansible -m ping host1`

##Excercises

- Check all running process on the node through Ansible
- Check free and used memory in nodes through Ansible
- Install vim on all the nodes using Ansible






