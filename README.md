# ansible_inventory
## Software environments for ansible_project.git

This is an Inventory repo for [ansible_project.git](https://github.com/playingfield/ansible_project.git).

# Requirements

### macOS computer

These programs can be installed manually.

### Apps
- VirtualBox
- Vagrant

# Vagrant Simulation

1. Boot the 4 Virtual Machine you'll need 8Gb free RAM.

```bash
vagrant up
```

2. Ansible configuration

Change the inventory line in `ansible_project/ansible.cfg`
```ini
[defaults]
host_key_checking = False
inventory = ../ansible_inventory/vagrant
```

# Automation Platform Simulation

This repo is read into Automation Controller by a definition in [ansible_controller](https://github.com/playingfield/ansible_controller). For the full experience boot the machines as described.
