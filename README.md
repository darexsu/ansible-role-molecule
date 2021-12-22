# ( NOT WORKING ) Molecule for Debian
Options:
  - install Molecule in virtualenv

Installation:
1) Install from Github (git installed on your server)
```
ansible-galaxy install git+https://github.com/darexsu/ansible-role-molecule.git
```
2) Example playbook
```
---
- hosts: all
  become: yes

  roles:
    - role: ansible-role-molecule
      vars:
        molecule_install: true
```
Testing:
1) activate virtualenv
```
source molecule/bin/activate
```
2) 
