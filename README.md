# docker-ubuntu-ansible
Docker container with Ubuntu base with Ansible installed.

[Dockerfile](Dockerfile/Dockerfile)

[Docker_Image](https://hub.docker.com/r/elbetho/ubuntu-ansible)

Built starting from [ubuntu:latest](https://hub.docker.com/_/ubuntu), which was Ubuntu 20.04.2 LTS.

## Installed: 
- Python3 - Needed to install and use Ansible
- python3-distutils - Needed to get pip to install correctly [1],[2]
- PIP - Used to install Ansible [1],[2]
- Curl - Used to download pip package and Ansible set-up documents [3]
- SSH - Needed in order to use Ansible
- nano - Convenient editor to make changes to Ansible files

To make a more usable version of Ansible inside the Docker container out of the gate, I also:
- Created `/etc/ansible` directory
- Created `/etc/ansible/roles` directory
- Copied example `ansible.cfg` file to `/etc/ansible`[3]
- Copied example `hosts` file to `/etc/ansible`[3]

## Further Steps:
In order to use this Docker version of Ansible, all that is left is to:
1. Input your inventory of machines to manage in hosts.  Include `ansible_python_interpreter=/usr/bin/python3` after the IP addresses to ensure things install correctly when using the playbooks.
2. Generate your SSH keys, if using.[4]
3. Make any changes to `ansible.cfg` needed to manage your set-up. For example, set `become_ask_pass` to `True` to prompt for a password, if needed.[5,6]
4. Generate your playbooks.
5. This Container would be a good fit for a Jump Box Provisioner, such as the one used in the ELK Stack deployment project: https://github.com/bethwjohnson/portfolio/tree/master/ELK_Stack_Deployment 

## References:

[1] https://pip.pypa.io/en/stable/installing/#upgrading-pip

[2] https://askubuntu.com/questions/1239829/modulenotfounderror-no-module-named-distutils-util

[3] https://github.com/ansible/ansible/tree/devel/examples

[4] https://www.raspberrypi.org/documentation/remote-access/ssh/passwordless.md

[5] https://docs.ansible.com/ansible/latest/reference_appendices/config.html

[6] https://stackoverflow.com/questions/25582740/missing-sudo-password-in-ansible

[7] https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.
html#installing-ansible-on-ubuntu

[8] https://hub.docker.com/_/ubuntu

[9] https://hub.docker.com/r/elbetho/ubuntu-ansible