# Ansible role Molecule (with Docker driver)
[![CI Molecule](https://github.com/darexsu/ansible-role-molecule/actions/workflows/ci.yml/badge.svg)](https://github.com/darexsu/ansible-role-molecule/actions/workflows/ci.yml)

Molecule testing:

| Platforms |    Debian     |    Ubuntu     |    CentOS     |  Rocky Linux |
| --------- | ------------- | ------------- | ------------- | ------------ |
|  Version  |   10, 11      | 18.04, 20.04  |     7, 8      |      8       |

Dependencies: Docker

Options:
  - install
    - ansible_user: sudo ( /home/user/.local/bin )
    - ansible_user: root  ( /usr/bin ) `not recommended`
  - install in virtualenv
    - ansible_user: sudo ( /home/user/molecule ) 
    - ansible_user: root ( /root/molecule ) `not recommended`
  

# Installation without virtualenv:
1) Install Docker

2) Install ansible-role from Galaxy
```
ansible-galaxy install darexsu.molecule
```
3) Example playbook
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

1) Ensure docker.service is running, and user in group "docker"
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
5) Ensure author without spaces in ./my_new_role/meta/main.yml
```
sed -i 's/author: your name/author: your_name/' ./meta/main.yml
```
6) testing
```
molecule test
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

1) Ensure docker.service is running, and user in group "docker"
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
5) Ensure author without spaces in ./my_new_role/meta/main.yml
```
sed -i 's/author: your name/author: your_name/' ./meta/main.yml
```
6) testing
```
molecule test
```
7) exit virtualenv
```
deactivate
```

