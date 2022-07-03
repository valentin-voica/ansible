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

### The Playbook

The `ubuntu-rpi.yaml` playbook configures the following:

* Update the cache and upgrade the system
* Configure PoE HAT fan thresholds
* Set the hostname in the `/etc/hosts` file
* Reboots the system if required
* Removes old packages from the cache
* Removes dependencies that are no longer needed
* Configures a static IP address in the Servers VLAN 30
* UFW firewall configurations

To run the playbook, make sure you are inside the directory containg the `passwd.yaml` file:

`$ cd ~/GitProjects/ansible/ubuntu`

`$ ansible-playbook --ask-vault-pass --extra-vars '@passwd.yaml' ~/GitProjects/ansible/ubuntu-rpi.yaml -l ubuntu.voica.lan -u pi`
