# Warhorse - Red Team Attack Infrastructure Automation


## CURRENT STATUS - BETA


Table of contents 
------------------
  * [Overview](#overview)
  * [Features](#features)
  * [Containers](#containers)
  * [Setup](#setup)
  * [Usage](#usage)
  * [Dependencies](#dependencies)
  
## Overview

Warhorse consist of a fully featured Ansible playbook to deploy infrastructure in the cloud for conducting covert “Red Team” Penetration test. This playbook is highly customizable and has operational security out of box. The design of this playbook is much more then automation. This playbook implements real world TTP’s to avoid detection, gather raw attack data, lower operational cost and speedup time to compromise. The primary goals of this project are to get software installed quickly and securely so tools can be used, and tactics can be implemented and shared. In addition, this project aims to lower deployment error and generate live attack intel that would otherwise not be gathered because of the time cost of creation and deployment.


## Features

* Pure Ansible playbook with low dependences and easy modification.
* Cloud provider support (AWS)
* Security from the ground up
	- White listed IP for management interfaces
	- Randomly generated passwords
	- Operating system hardening
	- Automated backup
	- Local Secret encryption with Ansible vault
	- API keys created per services that require them.
* Docker containers for each application. Avoids dependence issues and allows for the creation management and removal of complex software stacks.
* Low cost operation with single ec2 host.
* Easily add and remove docker containers to create a stack that fits your engagement
* Bottom up build everything is created and removed on damand


## Containers

### Management
* Traefik 
* Netdata
* Lair
* Watchtower
* Grafana (Coming Soon)
* Backup (Borg/rclone) (Coming Soon)

### Command And Control
* Cobalt Strike

### OSINT
* Spiderfoot (Coming Soon)

### Cloud Obfuscation
* API Gateway (Coming Soon)
* AWS Cloudfront (Coming Soon)
* C2 Redirectors (Coming Soon)


## Setup

### Requirements

- AWS API Key (Administrator Role)
- Domain Name added to route53
- Ansible 2.7
- Boto 2
- Boto 3
- awscli

If your on a new system, we'll need to do some preliminary tasks. Assuming we have git, Python, pip and other obvious essentials like Ansible installed, let's get started...

At a terminal, enter the following:

```bash
# Clone the project
git clone https://github.com/war-horse/warhorse

# Make sure awscli and boto are installed
pip install awscli boto boto3

# Configure aws credentials
aws configure
```

Help with AWS configuration can be found here: http://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html

```bash
# Setup a vault password
vi ~/.vault_passs
chmod 400 ~/.vault_pass

# Modifiy varables 
 inventory/group_vars/all/all.yml
 
```


## Usage

To launch the infrastructure, use the following command.

```bash
$ ansible-playbook -i inventory/hosts site.yml --vault-password-file ~/.vault_pass
```


## What's Next?

This project is rapidly evolving. I have plans to continue active devlopment and will utlize during my own engagments and modify and impove when necessary. I will be created better documentation as this project stabilizes. This playbook may not work at all feel free to make push request. 
    

## Dependencies

#### Ansible Roles
- https://galaxy.ansible.com/geerlingguy/nginx/
- https://galaxy.ansible.com/geerlingguy/security/


## Author Information

Ralph May

https://github.com/ralphte