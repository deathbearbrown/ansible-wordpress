Wordpress Ansible
===========
//todo
- [ ] put plugins in the inventory files and have them cloned via git


Local Development
=================

Prereqs:
- Vagrant: https://www.vagrantup.com/
- Virtual Box: https://www.virtualbox.org/
- Ansible: http://www.ansible.com/home

To start the dev environment run:

```` vagrant up ````

Wordpress will be installed on the VM. You can add/edit plugins and themes locally and it will sync with the VM

add the following to /etc/hosts:
`192.168.50.20 wp.dev`

When it's finished go to:
`http://wp.dev`

Set up wordpress



Deploying to Staging
====================

The staging inventory needs to be configured for the staging site.

Run the ansible playbooks using the following command:

`ansible-playbook --private-key=~/.ssh/staging.pem -i ansible/inventory/staging ansible/vagrant.yml -vvv`

where staging.pem is the pem key for your staging server


Copy changes to the VM
======================

When you want to copy changes from your wp-content folder to your local VM, run the following:

`ansible-playbook --private-key=~/.vagrant.d/insecure_private_key -i ansible/inventory/vagrant ansible/copy.yml -vvv`
