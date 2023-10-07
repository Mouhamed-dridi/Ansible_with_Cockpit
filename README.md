# Ansible Automation for Rocky Linux Servers

![Cockpit Logo](cockpit-logo.png)

## Overview

This Ansible project automates the installation of the Cockpit web interface on Rocky Linux servers. Cockpit is a web-based server management tool that simplifies server administration tasks. This repository provides step-by-step instructions and playbooks to configure Cockpit on your Rocky Linux servers.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
  - [Clone the Repository](#clone-the-repository)
  - [Edit the Inventory](#edit-the-inventory)
- [Usage](#usage)
  - [Ping Test](#ping-test)
  - [Install Cockpit](#install-cockpit)
- [Accessing Cockpit](#accessing-cockpit)


## Prerequisites

Before using this Ansible project, ensure that you have the following prerequisites in place:

- Two Rocky Linux servers with SSH access enabled.
- Ansible installed on your local machine.
- SSH access to the servers using key-based authentication.

## Getting Started

### Clone the Repository

To get started, clone this repository to your local machine:

```bash
git clone https://github.com/your-username/ansible-rocky-linux-cockpit.git
cd ansible-rocky-linux-cockpit
```

Certainly! I'll provide you with an updated README file that includes the added inventory information and instructions for installing sshpass on the servers, as well as creating a playbook to test the connection between Ansible and the nodes.

markdown
Copy code
# Ansible Automation for Rocky Linux Servers

![Cockpit Logo](cockpit-logo.png)

## Overview

This Ansible project automates the installation of the Cockpit web interface on Rocky Linux servers. Cockpit is a web-based server management tool that simplifies server administration tasks. This repository provides step-by-step instructions and playbooks to configure Cockpit on your Rocky Linux servers.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
  - [Clone the Repository](#clone-the-repository)
  - [Edit the Inventory](#edit-the-inventory)
  - [Install sshpass](#install-sshpass)
- [Usage](#usage)
  - [Ping Test](#ping-test)
  - [Install Cockpit](#install-cockpit)
- [Accessing Cockpit](#accessing-cockpit)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Prerequisites

Before using this Ansible project, ensure that you have the following prerequisites in place:

- Two Rocky Linux servers with SSH access enabled.
- Ansible installed on your local machine.
- SSH access to the servers using key-based authentication.

## Getting Started

### Clone the Repository

To get started, clone this repository to your local machine:

```bash
git clone https://github.com/your-username/ansible-rocky-linux-cockpit.git
cd ansible-rocky-linux-cockpit

## install  sshpass
 sshpass as a variable:

##  Edit the Inventory
Edit the inventory.ini  or create new one file to specify the IP addresses or hostnames of your Rocky Linux servers:
```[rocky_nodes]
rocky-node1 ansible_host=IP_ADDRESS1 ansible_user=YOUR_SSH_USER
rocky-node2 ansible_host=IP_ADDRESS2 ansible_user=YOUR_SSH_USER
```

## Step 3: Create Ansible Playbooks
a. Ping Test Playbook (ping.yml):
Create a playbook to test the connection to your Rocky Linux nodes.
```
---
- name: Ping Test
  hosts: rocky_nodes
  tasks:
    - name: Ping the Rocky Linux nodes
      ping:

```
## Cockpit Installation Playbook (install-cockpit.yml)
Create a playbook to install Cockpit on your Rocky Linux nodes.
```
---
- name: Install Cockpit on Rocky Linux
  hosts: rocky_nodes
  become: yes
  tasks:
    - name: Update package cache
      apt:
        update_cache: yes

    - name: Install Cockpit
      package:
        name: cockpit
        state: present

    - name: Start Cockpit service
      service:
        name: cockpit
        state: started
        enabled: yes
```

## Step 4: Run Ansible Playbooks
Now, you can run the Ansible playbooks you've created

Ping Test:
Run the ping.yml playbook to check the connection to your Rocky Linux nodes:
```
ansible-playbook -i inventory.ini ping.yml
```

Install Cockpit:
Run the install-cockpit.yml playbook to install Cockpit on your Rocky Linux nodes:
```
ansible-playbook -i inventory.ini install-cockpit.yml --ask-becom
```

## Step 5: Access Cockpit Web Interface
After running the install-cockpit.yml playbook, you can access the Cockpit web interface on each Rocky Linux node by opening a web browser and entering the server's IP address or hostname followed by port 9090 (e.g., http://server-ip:9090). Make sure that port 9090 is accessible in your firewall settings.

That's it! You've successfully set up Ansible to manage two Rocky Linux nodes from your Debian master server and installed Cockpit on them using Ansible playbooks. You can now expand your automation by creating additional playbooks for other tasks or configurations.



