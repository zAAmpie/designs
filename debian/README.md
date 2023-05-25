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
- Open interface file
	```bash
	nano /etc/network/interfaces
	```
- Add static IP
	```bash
	iface ens18 inet static
		address 10.10.13.1/16
		gateway 10.10.0.1
		dns-nameservers 1.1.1.1 1.0.0.1
	```
- Restart networking service 
	```bash
	service networking restart
	```
- Bring up interface
	```bash
	ifup ens18
	```
- Edit sshd config and add `PermitRootLogin yes` to file
	```bash
	nano /etc/ssh/sshd_config
	```
- Restart SSH service
	```bash
	service ssh restart
	```
- Add IP to staging inventory file on `jump.drsam.cc`
	```bash
	cd ~/boilerplate/ansible/staging/
	nano inventory
	```
- Stage the host for Ansible
	```bash
	ansible-playbook minimal_setup.yaml
	```
- As IP to main inventory file under `[staging]` on `jump.drsam.cc`
	```bash
	cd ~/boilerplate/ansible
	nano inventory
	```
- Set up Debian using Ansible playbook
	```bash
	ansible-playbook minimal_debian.yaml
	```

