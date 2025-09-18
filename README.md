# ELK using ansible

In this project, we are configuring ELK stack on single node using docker, docker-compose and ansible with role logging_single_node.
In this project, we are configuring ELK stack on cluster of nodes using docker, docker-compose and ansible with role logging_cluster.

## Getting Started

vault password is : password

Preinstall : ansible-playbook -i inventory.ini playbooks/preinstall.yml --tags provision --ask-vault-pass -kK

Ansible commands to install ELK stack cluster :
ansible-playbook -i inventory.ini postinstall.yml --tags add_elasticsearch --ask-vault-pass -kK
