# Setup Apigee OPDK Ansible Configuration Accelerator

## Introduction
An Ansible controller is used to run Ansible playbooks. This repository contains playbooks that 
configure an Ansible controller. The role [Apigee OPDK Setup Ansible Controller](https://github.com/carlosfrias/apigee-opdk-setup-ansible-controller) 
is used to configure an Ansible Controller and should be consulted for additional details. This 
setup provides you with a common configuration convention that simplifies managing either one planet 
or several planets of any size.  

## Assumptions
* Ansible is installed on the server set aside as an Ansible Controller. 
* The `setup.yml` playbook uses the [Apigee OPDK Setup Ansible Controller](https://github.com/carlosfrias/apigee-opdk-setup-ansible-controller) 
role to configure an Ansible controller to use the framework. The `setup.yml` assumes that the you 
are configuring the localhost. 
* Same setup for either a single planet or multiple planets.
* The user home will be used to create the folders `~/.ansible`, `~/.apigee`, `~/.apigee-secure`, 
and `~/apigee-workspace`.
* The folder `~/apigee-workspace` will be used to contain playbooks. Use 
`git clone https://github.com/carlosfrias/apigee-opdk-playbook-installation-single-region.git`to get 
started.
* You must provde the name of the remote user that will be used for SSH access. This cannot be the 
`apigee` user.
* `ssh` access is working to target servers that will be a part of the Apigee planet.

### Configure SSH Access for your Nodes
A helper playbook is provided for the common task of configuring SSH access to enable the use of 
SSH keys for greater security. Please see 
[Configure SSH Login ](configure-ssh-login) 
for details. 

### Backup an Ansible Control Server
A helper playbook is provided for the common task of backing up the configurations managed by the 
Ansible control to another file system location. Please see 
[Ansible Control Server Backup](backup-ansible-controller) for details.

# Usage Instructions

## Download Dependencies
Use `ansible-galaxy` to download dependencies in the following way: 

    # Download the required roles to setup the Ansible controller
    ansible-galaxy install -r requirements.yml -f

## Setup an Ansible Control Server on localhost

`setup.yml` will configure the localhost as an Ansible control server in the following way:
    
    # Setup the Ansible controller
    ansible-playbook setup.yml -e remote_user=<remote user login>