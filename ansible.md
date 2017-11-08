# Ansible
|Option|Description|
|:-----|:----------|
| `-m [command,apt,yum,ping,service,file,etc]` | Module, optional, command is defualt |
| `-a [uptime,cal,'tail /etc/crontab','name=nginx','... state=restarted']` | module command |
| `-i /path/inventory` | inventory file |
| `-e EXTRA_VARS` | env |
| `-s` | DEPRECATED, use -b |
| `-b [sudo,pbrun]` | run as sudo |
| `-C` | dont make any changes; try to predict |
| `-D` | when changing, show diff of files, works with -C |

``` $ ansible server -a uptime (-m command is default)```

### Ansible without hosts file
```$ ansible all -i [example.com/IP], ```
### Requires 'hosts: all' in your playbook
```$ ansible-playbook -i host.oracle.com, playbook.yml```

## get facts
```bash
$ ansible server -m setup [-a 'filter=ansible_*_mb']

  - set_fact: fact_name={{ result.stdout }}
```

## Playbook
```yaml
---
- name: Configure server X
  hosts: webservers
  [gather_facts: yes]
  become: yes
  become_method: sudo
[ vars:
    proxy_env:
      http_proxy: www-proxy.com:80
      https_proxy: www-proxy.com:80
      ftp_proxy: www-proxy.com:80
      ftps_proxy: www-proxy.com:80
    server_name: localhost] or and
[ vars_files:
    - file.yml ]
  roles:
    - docker
  tasks:
    - name: install X
      apt: name=x update_cache=yes

    - name: enable it
      file: >
        dest=/etc/x
        src=/etc/y
        state=link
      ignore_errors: True
    - debug: var=myvarname / msg="My message is {{myvarname}}"
  environment: '{{proxy_env}}'
```
##  docs
```
$ ansible-doc [module_name]
  -l | list
```
##  Inventory
```
vm1 ansible_host=127.0.0.1 color=blue
vm2 ansible_host=127.0.0.1 color=red
[group_name]
vm1
[all:children]
group_name
group_name2
[group_name:vars]
db_user=mysqlusr
rabbitmq_port=5672
```
```
group_vars/group_name
db_user=mysqlusr
rabbitmq_port=5672
```
##  Built in Variables
```
hostvars | Dict with keys are Ansible hostnames and values dict to variable names
         | {{ hostsvars['db.example.com'].ansible_eth1.ipv4.address }}
inventory_hostname | Name of the CURRENT host known by Ansible (the alias)
                   | hostvars[inventory_hostname]
group_names | All groups current host is member
groups | dict with all groups
       | groups.group_name -> gets all hosts
play_hosts | List of inventory hostnames active in current play
ansible_version | :#!/bin/sh
```
## ansible-playbook
```
  --list-tasks | print all names
  --start-at-task='Install HAProxy'
```
