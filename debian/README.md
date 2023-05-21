# Debian best practices

## Installation

During installation, these are the standard steps to consider

1. Root password should be standard long
2. Additional username should be `sam`, with password `sam` for initial setup
3. Run Ansible setup in `boilerplate/ansible/staging/minimal_setup.yaml` to stage for Ansible
4. Run Ansible setup in `boilerplate/ansible/minimal_debian.yaml` to update/upgrade
