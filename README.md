# ANSIBLE
A collection of Ansible plays

## Ubuntu Server 20.04 LTS on Raspberry Pi 4 with PoE HAT - Initial Configuration

This playbook configures the following:

* Update the cache and upgrade the system
* Configure PoE HAT fan thresholds
* Set the hostname
* Reboots the system if required
* Removes old packages from the cache
* Removes dependencies that are no longer needed
* Configures a static IP address in the Servers VLAN

To run the playbook, make sure you are inside the directory containg the `passwd.yaml` file:

`$ cd ~/GitProjects/ansible/ubuntu`

`$ ansible-playbook --ask-vault-pass --extra-vars '@passwd.yaml' ~/GitProjects/ansible/playbook.yaml -l ubuntu.voica.lan -u pi`
