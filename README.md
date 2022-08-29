Business Case: You need to setup ansible automation to

Automate linux machines configuration(yum installation, DNS setting) to join them in Windows ACtive directory
Automate adding Windows domain users to linux machines sudoer's file
Automate add public ssh keys from ansible controller to ansible targets
Configuration of Ansible vault to encrypt credentials located in ansible contrller to secure password connection to ansible targets

In this lab I used VMware Wokstation and setup their network in Virtual Network Editor
I also set the machines to have static IP as I have not built dedciated DHCP server for them
DNS server is also in Active directory server so I set the DNS hostname of the machines there

Create 4 VMs

Create domain: gracepractice.com

ansiblecontroller - 192.168.150.2 
ansibletarget1 - 192.168.150.3 
ansibletarget2 - 192.168.150.4 
Windows Active directory(DNS server) - 192.168.150.9

Domain Admins: 
mzabala 
rabejuela 
scalma 
rcalma 
maicalma

Steps

Problem 1: Copy public ssh keys from ansiblecontroller to ansible target 1 and ansible target2 Take Note: Upon copying public ssh keys, you stll have no sudo install some application in linux
Problem 2: Create Ansible Vault to encrypt yourlinux ssh password. You will also need it to securely access linux target machines via sudo 
Problem 3: Build Windows Server 2022 that will act as Active Directory and DNS server. Create users there that will become domain admins 
Problem 4: Configure Linux servers Domain/DNS settings to join and authenticate to our windows active directory Problem 5: Add users created in WIndows Active directory to sudoers file of our linux machines

There is also role setup under play directory to convert the csv file to dictionary

ssh public key copier is in roles also. You must put all your ssh keys in files/keys in order to copy them in remote authorized public keys

To run the playbook, execute ansible-playbook play/project_1.yml --ask-vault-pass
