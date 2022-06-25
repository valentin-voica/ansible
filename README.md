# ANSIBLE
A collection of Ansible plays

## Ubuntu Server 20.04 LTS - Initial Configuration

### Static IP address:

`$ ansible-playbook playbook_static_ip_ub2004.yaml -i inventory_staging.yaml -K`

This Ansible playbook downloads the static IP address configuration file from the `configs` repo, applies the change, then, after a 10 seconds delay, restarts the system.

### Other tasks

* Update the cache and upgrade the system
* Configure PoE HAT fan thresholds (Raspberry Pi only)
* 
