# ANSIBLE
A collection of Ansible plays

## Ubuntu Server 20.04 LTS - Initial Configuration

### Tasks

`$ cd ~/GitProjects/ansible/ubuntu`

`$ ansible-playbook --ask-vault-pass --extra-vars '@passwd.yaml' ~/GitProjects/ansible/playbook.yaml -l ubuntu.voica.lan -u pi`

This playbook configures the following:

* Update the cache and upgrade the system
* Configure PoE HAT fan thresholds (Raspberry Pi only)
* Set the hostname
* Reboots the system if required
* Removes old packages from the cache
* Removes dependencies that are no longer needed
* Configures a static IP address in the Servers VLAN
