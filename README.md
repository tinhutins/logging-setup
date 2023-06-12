# Prometheus with Grafana using Ansible

In this project, we are configure ELK stack on single node using docker, docker-compose and ansible.

## Getting Started

vault password is : password


Ansible command to install ELK stack : ansible-playbook -i inventory.yml playbook.yml --tags logging --ask-vault-pass -kK