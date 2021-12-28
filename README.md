# Ansible role Molecule (with Docker driver)
[![CI Molecule](https://github.com/darexsu/ansible-role-molecule/actions/workflows/ci.yml/badge.svg)](https://github.com/darexsu/ansible-role-molecule/actions/workflows/ci.yml)
Ansible dependencies: None

Molecule dependencies: Ansible, Docker

Platforms: Debian, Ubuntu, RHEL, CentOS, Rocky, Oracle

Options:
  - Molecule, ansible_user: sudo [ /home/user/.local/bin ]
  - Molecule, ansible_user: root  [ /usr/bin ]                          not recommended
  - Molecule in virtualenv ansible_user: sudo [ /home/user/molecule ] 
  - Molecule in virtualenv ansible_user: root [ /root/molecule ]        not recommended
  

# Installation without virtualenv:
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
      vars:
        molecule_install: true        
```
Testing:

1) Ensure docker.servise is running, and user in group "docker"
```
systemctl status docker
```
2) You have to re-login. if you have already logged as molecule-user.
```
exit
```
3) init test role
```
molecule init role my_new_role --driver-name docker
```
4) go to folder of role
```
cd ./my_new_role
```
5) enter author without spaces in ./my_new_role/meta/main.yml
```
sed -i 's/author: your name/author: your_name/' ./meta/main.yml
```
6) testing
```
molecule test
```
7) destroy docker instance
```
molecule destroy
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
      vars:
        molecule_install: true
        molecule_install_virtualenv: true
```
Testing:

1) Ensure docker.servise is running, and user in group "docker"
```
systemctl status docker
```
2) activate virtualenv
```
source molecule/bin/activate
```
3) init test role
```
molecule init role my_new_role --driver-name docker
```
4) go to folder of role
```
cd ./my_new_role
```
5) enter author without spaces in ./my_new_role/meta/main.yml
```
sed -i 's/author: your name/author: your_name/' ./meta/main.yml
```
6) testing
```
molecule test
```
7) destroy docker container
```
molecule destroy
```
8) exit virtualenv
```
deactivate
```

