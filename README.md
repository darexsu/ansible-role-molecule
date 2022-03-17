# Ansible role: Molecule
[![CI Molecule](https://github.com/darexsu/ansible-role-molecule/actions/workflows/ci.yml/badge.svg)](https://github.com/darexsu/ansible-role-molecule/actions/workflows/ci.yml)&emsp;![Ansible Role](https://img.shields.io/ansible/role/d/57358?color=blue&label=downloads)


  - Role:
      - [platforms](#platforms)
      - [install](#install)
      - [merge behaviour](#merge-behaviour)
  - Playbooks (merge version):
      - [install and configure: Molecule](#install-and-configure-molecule-merge-version)
  - Playbooks (full version):
      - [install and configure: Molecule](#install-and-configure-molecule-full-version)

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

### Merge behaviour

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

### Install and configure: Molecule (merge version)

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
### Install and configure: Molecule (full version)

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
      packages: [ansible-core, molecule, "molecule[docker]", "molecule[lint]"]

  tasks:
    - name: include role darexsu.molecule
      include_role:
        name: darexsu.molecule
```