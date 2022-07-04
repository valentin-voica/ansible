# ANSIBLE
A collection of Ansible plays

## Ubuntu Server 20.04 LTS on Raspberry Pi 4 with PoE HAT - Initial Configuration

### Preparing the SD card

Write the SD card using Raspberry Pi Imager

* Operating System: "UBUNTU SERVER 20.04.4 LTS (RPI 3/4/400)"
* Storage: SD card
* Advanced Options
  * "Set hostname" check-box ticked; hostname: ubuntu
  * "Enable SSH" check-box ticked; select "Allow public-key authentication only" and enter the content of the `id_rsa.pub` file from the client system
  * "Set username and password" check-box ticked; Username: `pi` | Password: `***************`
  * "Configure wireless LAN" check-box un-ticked
  * "Set locale settings" check-box ticked; Time zone: Europe/London | Keyboard layout: gb
* Click the "WRITE" button

### The Inventory

Make sure the relevant information is correct

* "ubuntu.voica.lan" must always be in the "hosts:" group
* The `passwd.yaml` is in the `~/GitProjects/ansible/ubuntu` directory

### The Playbooks

To run these playbooks, make sure you are inside the directory containg the `passwd.yaml` file:

`$ cd ~/GitProjects/ansible/ubuntu`

#### `ubuntu-rpi.yaml` playbook

This playbook configures the following:

* Update the cache and upgrade the system
* Configure PoE HAT fan thresholds
* Set the hostname in the `/etc/hosts` file
* Reboots the system if required
* Removes old packages from the cache
* Removes dependencies that are no longer needed
* Configures a static IP address in the Servers VLAN 30
* UFW firewall configurations

`$ ansible-playbook --ask-vault-pass --extra-vars '@passwd.yaml' ~/GitProjects/ansible/ubuntu-rpi.yaml -l ubuntu.voica.lan -u pi`

#### `install-docker.yaml` playbook

The playbook adds on top of the previous one installing and configuring Docker. It was built by following the tutorial at [How to Use Ansible to Install and Set Up Docker on Ubuntu 20.04](https://www.digitalocean.com/community/tutorials/how-to-use-ansible-to-install-and-set-up-docker-on-ubuntu-20-04).

`$ ansible-playbook --ask-vault-pass --extra-vars '@passwd.yaml' ~/GitProjects/ansible/install-docker.yaml -l ubuntu.voica.lan -u pi`

