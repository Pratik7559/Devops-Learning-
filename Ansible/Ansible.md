# ⚙️ Ansible Zero to Hero

## What is Ansible?
Ansible is an open-source automation and configuration-management tool used for server configuration, application deployment, provisioning, and orchestration.

## Why Ansible?
- Configuration Management
- Application Deployment
- Server Provisioning
- Automation
- Orchestration
- Agentless Architecture
- Idempotent Operations

## Architecture

```text
Ansible Control Node
        |
   SSH / WinRM
        |
  Managed Nodes
```

### Control Node
The machine from which Ansible commands and playbooks are executed.

### Managed Nodes
Servers or machines managed by Ansible.

### Inventory
A file containing the hosts Ansible manages.

### Playbook
A YAML file containing automation tasks.

### Module
A reusable unit that performs a specific operation.

## Agentless Architecture

Linux managed nodes commonly use SSH:

```text
Ansible → SSH → Managed Server
```

## Installation

Ubuntu/Debian:

```bash
sudo apt update
sudo apt install ansible -y
ansible --version
```

## Inventory

```ini
[webservers]
web1 ansible_host=192.168.1.10
web2 ansible_host=192.168.1.11

[dbservers]
db1 ansible_host=192.168.1.20
```

Check inventory:

```bash
ansible-inventory --list
```

## Ad-Hoc Commands

```bash
ansible all -m ping
ansible all -m command -a "uptime"
ansible all -m shell -a "df -h"
```

## Playbooks

Example:

```yaml
---
- name: Install Nginx
  hosts: webservers
  become: true

  tasks:
    - name: Install Nginx
      apt:
        name: nginx
        state: present

    - name: Start Nginx
      service:
        name: nginx
        state: started
        enabled: true
```

Run:

```bash
ansible-playbook install-nginx.yml
```

## Important Keywords

### hosts
Defines the target hosts or inventory group.

### become
Used for privilege escalation.

```yaml
become: true
```

### tasks
Contains operations to perform.

### name
Provides a readable task name.

## Important Modules

- `apt` / `dnf` / `yum` — package management
- `service` / `systemd` — services
- `copy` — copy files
- `file` — files and directories
- `template` — Jinja2 templates
- `command` — execute commands
- `shell` — execute shell commands
- `user` — manage users
- `group` — manage groups

## Variables

```yaml
vars:
  package_name: nginx

tasks:
  - name: Install package
    apt:
      name: "{{ package_name }}"
      state: present
```

## Handlers

Handlers run when notified by another task.

```yaml
tasks:
  - name: Copy configuration
    copy:
      src: nginx.conf
      dest: /etc/nginx/nginx.conf
    notify: Restart Nginx

handlers:
  - name: Restart Nginx
    service:
      name: nginx
      state: restarted
```

## Conditions

```yaml
- name: Install Nginx
  apt:
    name: nginx
    state: present
  when: ansible_os_family == "Debian"
```

## Loops

```yaml
- name: Install packages
  apt:
    name: "{{ item }}"
    state: present
  loop:
    - nginx
    - git
    - curl
```

## Templates

Ansible uses Jinja2 templates for dynamic configuration.

```jinja2
server_name {{ server_name }};
```

```yaml
- name: Deploy configuration
  template:
    src: nginx.conf.j2
    dest: /etc/nginx/nginx.conf
```

## Roles

Roles organize reusable Ansible automation.

```text
roles/
└── nginx/
    ├── tasks/main.yml
    ├── handlers/main.yml
    ├── templates/
    ├── files/
    ├── vars/
    ├── defaults/
    └── meta/
```

## Ansible Vault

Used to encrypt sensitive data.

```bash
ansible-vault create secrets.yml
ansible-vault edit secrets.yml
ansible-vault encrypt secrets.yml
ansible-vault decrypt secrets.yml
```

## Ansible Galaxy

Used to find and share Ansible roles and collections.

```bash
ansible-galaxy init nginx
```

## ansible.cfg

Common configuration file:

```ini
[defaults]
inventory = ./inventory
remote_user = ubuntu
host_key_checking = False
```

## Ansible + AWS

A common DevOps workflow:

```text
Terraform
   ↓
AWS Infrastructure
   ↓
EC2
   ↓
Ansible
   ↓
Application Configuration
```

Terraform provisions infrastructure; Ansible configures servers and applications.

## Ansible + Jenkins

```text
Developer
   ↓
GitHub
   ↓
Jenkins
   ↓
Build & Test
   ↓
Ansible
   ↓
Deployment
```

## Ansible vs Terraform

| Feature | Ansible | Terraform |
|---|---|---|
| Main purpose | Configuration & automation | Infrastructure as Code |
| Language | YAML | HCL |
| State | No Terraform-style state | Uses state |
| Typical use | Configure servers/apps | Provision infrastructure |
| Architecture | Agentless | Provider-based |

## Best Practices

- Use Git for playbooks.
- Use variables instead of hardcoding.
- Use roles for reusable automation.
- Use Ansible Vault for secrets.
- Prefer idempotent modules over raw shell commands.
- Test playbooks before production.
- Keep tasks small and readable.
- Use meaningful names.

## Common Commands

```bash
ansible --version
ansible all -m ping
ansible-inventory --list
ansible all -m setup
ansible-playbook playbook.yml
ansible-playbook --check playbook.yml
ansible-playbook --syntax-check playbook.yml
ansible-galaxy init role_name
ansible-vault create secrets.yml
```

## Interview Questions

1. What is Ansible?
2. Why is Ansible agentless?
3. What is a control node?
4. What is a managed node?
5. What is an inventory?
6. What is a playbook?
7. What is a module?
8. What is idempotency?
9. What are handlers?
10. What are roles?
11. What is Ansible Vault?
12. `command` vs `shell`?
13. What is `become`?
14. What are loops and conditions?
15. Ansible vs Terraform?
16. How do you integrate Ansible with Jenkins?
17. How can Terraform and Ansible be used together?

## Learning Checklist

- [ ] Install Ansible
- [ ] Control Node
- [ ] Managed Nodes
- [ ] Inventory
- [ ] Ad-Hoc Commands
- [ ] Modules
- [ ] Playbooks
- [ ] Variables
- [ ] Handlers
- [ ] Conditions
- [ ] Loops
- [ ] Templates
- [ ] Roles
- [ ] Ansible Vault
- [ ] Ansible Galaxy
- [ ] ansible.cfg
- [ ] AWS Integration
- [ ] Jenkins Integration
- [ ] Terraform + Ansible Project

---

## 🎯 DevOps Takeaway

**Terraform can provision infrastructure, while Ansible can configure and deploy applications on that infrastructure. Together they form a powerful Infrastructure as Code and configuration-management workflow.**
