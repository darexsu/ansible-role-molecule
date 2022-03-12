# Ansible role: Molecule with Docker driver
[![CI Molecule](https://github.com/darexsu/ansible-role-molecule/actions/workflows/ci.yml/badge.svg)](https://github.com/darexsu/ansible-role-molecule/actions/workflows/ci.yml)&emsp;![Ansible Role](https://img.shields.io/ansible/role/d/57358?color=blue&label=downloads)

|  Testing         |  Ready for use      |
| :--------------: | :----------------:  |
| Debian 11        |  :heavy_check_mark: |
| Debian 10        |  :heavy_check_mark: |
| Ubuntu 20.04     |  :heavy_check_mark: |
| Oracle Linux 8   |  :heavy_check_mark: |
| Rocky Linux 8    |  :heavy_check_mark: |

Replace or Merge dictionaries (with "hash_behaviour=replace" in ansible.cfg):
```
# Replace             # Merge
---                   ---
  vars:                 vars:
    dict:                 merge:
      a: "value"            dict: 
      b: "value"              a: "value" 
                              b: "value"

# How does merge work?
Your vars [host_vars]  -->  default vars [current role] --> default vars [include role]
  
  dict:          dict:              dict:
    a: "1" -->     a: "1"    -->      a: "1"
                   b: "2"    -->      b: "2"
                                      c: "3"
    
```

##### 1) Install from Galaxy
```
ansible-galaxy install darexsu.molecule --force
```
##### 2) Example playbook: install molecule

requirements: ansible_user: "not root"

```yaml
---
- hosts: all
  become: true

  vars:
    merge:
      # Molecule
      molecule:
        enabled: true
      # Molecule -> install
      molecule_install:
        enabled: true
  
  tasks:
  - name: include role darexsu.molecule
    include_role: 
      name: darexsu.molecule   
```