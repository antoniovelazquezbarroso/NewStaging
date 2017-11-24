#  README

$ ansible-galaxy install -r requirements.yml

To install the required roles defined at requirements.yml
The installation folder is /roles because of the configuration in ansible.cfg
If you re-install the roles (from ansible-galaxy), check for required amendments at:
  - role mysql/tasks/users.yml, añadir ignore_errors= true en linea 13
  - role nrpe-client/tasks/main.yml añadir validate_certs=no al final de linea 17 (task Get NRPE)


To provision with vagrant just run vagrant up
To provision with digital ocean or AWS
Uncomment in /playbooks/provision.yml file the provisioner to be used
Play the /playbooks/provision.yml playbook on the corresponding inventory file

$ ansible-playbook -i inventories/digitalocean/inventory playbooks/provision.yml
$ ansible-playbook -i inventories/aws/inventory playbooks/provision.yml


Building the VMs

  1. Download and install [VirtualBox](https://www.virtualbox.org/wiki/Downloads).
  2. Download and install [Vagrant](http://www.vagrantup.com/downloads.html).
  3. [Mac/Linux only] Install [Ansible](http://docs.ansible.com/intro_installation.html).
  4. Run `ansible-galaxy install -r requirements.yml` in this directory to get the required Ansible roles.
  5. Run `vagrant up` to build the VMs and configure the infrastructure.
