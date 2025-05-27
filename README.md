# Automate Webserver Setup Using Ansible Roles and Handlers

 This repository demonstrates how to use **Ansible roles** to automate the installation and configuration of a web server (like Apache or Nginx) across multiple environments — specifically **demo** and **production**.

## Prupose 
This repository is designed for:

- DevOps engineers and beginners learning Ansible roles
- Automating web server deployment consistently across environments
- Demonstrating clean role-based architecture for reusable Ansible code

## Prerequisites

- A control machine with **Ansible installed**
- SSH access to your target demo and prod nodes
- Ansible-compatible systems (Ubuntu, CentOS, etc.)

## 🚀 How to Use

### 1. Clone the Repository

         git clone https://github.com/your-username/ansible-webserver-roles.git
         cd ansible-webserver-roles

### 2. Customize Inventory

You need to edit the files under inventory/demo and inventory/prod to include the IP addresses or hostnames of your target machines.

        [webservers]
        host1 ansible_host=<host-ip> ansible_user=ubuntu
        host2 ansible_host=<host-ip> ansible_user=ubuntu

### 3.  Review Defaults
 
 you can check and modify default variables if needed:

         # roles/webserver/defaults/main.yml
            web_package: apache2
            web_service: apache2

### 4.  Run the Playbook

        ansible-playbook -i inventory/demo playbook.yml
        ansible-playbook -i inventory/prod playbook.yml

##  What the Role Does
The webserver role:

- Installs a web server (apache2 by default)
- Starts and enables the web server service
- Optionally deploys a custom homepage using a Jinja2 template (if provided in templates/)