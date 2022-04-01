# Ansible role: Molecule
[![CI Molecule](https://github.com/darexsu/ansible-role-molecule/actions/workflows/ci.yml/badge.svg)](https://github.com/darexsu/ansible-role-molecule/actions/workflows/ci.yml)&emsp;![Ansible Role](https://img.shields.io/ansible/role/d/57358?color=blue&label=downloads)


  - Role:
      - [platforms](#platforms)
      - [install](#install)
  - Playbooks:
      - [install: Molecule](#install-molecule)

### Platforms

|  Testing         |  Ready for use      |
| :--------------: | :----------------:  |
| Debian 11        |  :heavy_check_mark: |
| Debian 10        |  :heavy_check_mark: |
| Ubuntu 20.04     |  :heavy_check_mark: |
| Oracle Linux 8   |  :heavy_check_mark: |
| Rocky Linux 8    |  :heavy_check_mark: |

### Install

```
ansible-galaxy install darexsu.molecule --force
```

### Install: Molecule

requirements: ansible_user: "not root"

```yaml
---
- hosts: all
  become: true

  vars:
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