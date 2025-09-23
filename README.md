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

Default vault password: 
  ```bash
  password 
  ```


# Install whole ELK Cluster with additional services

1. Add Elasticsearch nodes:

  ```bash
  ansible-playbook -i inventory.ini playbooks/postinstall.yml --tags add_elasticsearch --ask-vault-pass -kK
  ```

2. Add Kibana:

  ```bash
  ansible-playbook -i inventory.ini playbooks/postinstall.yml --tags add_kibana --ask-vault-pass -kK
  ```

3. Add Logstash:

  ```bash
  ansible-playbook -i inventory.ini playbooks/postinstall.yml --tags add_logstash --ask-vault-pass -kK
  ```

4. Add filebeat:

  ```bash
  ansible-playbook -i inventory.ini playbooks/postinstall.yml --tags add_filebeat --ask-vault-pass -kK
  ```

5. Add fleet:

  ```bash
  ansible-playbook -i inventory.ini playbooks/postinstall.yml --tags add_fleet --ask-vault-pass -kK
  ```
