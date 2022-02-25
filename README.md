# Ansible role Molecule (with Docker driver)
[![CI Molecule](https://github.com/darexsu/ansible-role-molecule/actions/workflows/ci.yml/badge.svg)](https://github.com/darexsu/ansible-role-molecule/actions/workflows/ci.yml)&emsp;![Ansible Role](https://img.shields.io/ansible/role/d/57358?color=blue&label=downloads)

| Testing |    Debian     |    Ubuntu     |    Rocky Linux     |  Oracle Linux |
| --------- | ------------- | ------------- | ------------- | ------------ |
|  Version  |   10, 11      | 18.04, 20.04  |      8        |       8       |

Options:
  - [install](#installation)
    - ansible_user: sudo ( /home/user/.local/bin )
    - ansible_user: root  ( /usr/bin ) `not recommended`
  - [install in virtualenv](#installation-in-virtualenv)
    - ansible_user: sudo ( /home/user/molecule ) 
    - ansible_user: root ( /root/molecule ) `not recommended`
  

### Installation:
1) Install from Galaxy
```
ansible-galaxy install darexsu.molecule
```
2) Example playbook
```yaml
---
- hosts: all
  become: yes

  roles:
    - role: darexsu.molecule
      # ------ install
      molecule_install: true        
```

# Installation in virtualenv:
1) Install from Galaxy
```
ansible-galaxy install darexsu.molecule
```
2) Example playbook
```yaml
---
- hosts: all
  become: yes

  roles:
    - role: darexsu.molecule
      # ------ install
      molecule_install: true
      molecule_install_virtualenv: true
```

