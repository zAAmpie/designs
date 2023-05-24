# Debian best practices

## Installation

Installation time ~7mins on picard

During installation, these are the standard steps to consider

- Root password should be standard long
- Additional username should be `sam`, with password `sam` for initial setup
- Use full disk with LVM
- Don't install desktop environment (KDE/Gnome)
- Install standard system utilities, SSH server

## After install

- Log in as root
- Run `nano /etc/network/interfaces`
- Add static IP
	```
	iface ens18 inet static
		address 10.10.13.1/16
		gateway 10.10.0.1
		dns-nameservers 1.1.1.1 1.0.0.1
	```
- Restart networking service `service networking restart`
- Bring up interface `ifup ens18`
- Run `nano /etc/ssh/sshd_config` and add `PermitRootLogin yes` to file
- Restart SSH service `service ssh restart`

- Go to `boilerplate/ansible/staging/` on `jump` and add IP above to inventory file
- Run `ansible-playbook minimal_setup.yaml` to stage for Ansible

- Go to `boilerplate/ansible` on `jump` and add IP to main `inventory` file
- Run `ansible-playbook minimal_debian.yaml` to update/upgrade

