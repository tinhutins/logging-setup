# Automated ELK stack install using ansible

## We provide two roles for ELK stack installation:

- Single-node ELK stack
  Role: logging_single_node

- Clustered ELK stack
  Role: logging_cluster

Everything is automated via  **Ansible playbooks**.

---

## 📋 Prerequisites

- Ubuntu **22.04 LTS** system(s)  
- Ansible installed on your control node  
- SSH access to target hosts  
- Vault password (see below)  

---


## ⚡ Quick Start

1. Clone the repository:

   ```bash
   git clone https://github.com/tinhutins/logging-setup.git
   cd logging-setup

2. Verify your inventory.ini matches your environment.

3. Run the pre-install provisioning step:

    ```bash
    ansible-playbook -i inventory.ini playbooks/preinstall.yml --tags provision --ask-vault-pass -kK
    ```
  -  NOTE: This step uses the local user tino on machines with sudo privileges. Make sure to update playbooks/preinstall.yml if you need to use a different user.

Default vault password: 
  ```bash
  password 
  ```

# Install whole ELK Cluster with additional services

1. Add Elasticsearch nodes:

  ```bash
  ansible-playbook -i inventory.ini playbooks/postinstall.yml --tags add_elasticsearch --ask-vault-pass
  ```

2. Add Kibana:

  ```bash
  ansible-playbook -i inventory.ini playbooks/postinstall.yml --tags add_kibana --ask-vault-pass
  ```

3. Add Logstash:

  ```bash
  ansible-playbook -i inventory.ini playbooks/postinstall.yml --tags add_logstash --ask-vault-pass
  ```

4. Add Filebeat:

  ```bash
  ansible-playbook -i inventory.ini playbooks/postinstall.yml --tags add_filebeat --ask-vault-pass
  ```

5. Add Fleet:

  ```bash
  ansible-playbook -i inventory.ini playbooks/postinstall.yml --tags add_fleet --ask-vault-pass
  ```
