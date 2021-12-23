# Molecule for Debian. Docker
Options:
  - install Molecule in user home directory
  - install Molecule in virtualenv
Dependencies:
  - Ansible
  - Docker
# Installation user home directory:
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
        molecule_install_virtualenv: true
```
Testing:
1) init test role
```
molecule init role my_new_role --driver-name docker
```
2) go to folder of role
```
cd ./my_new_role
```
3) enter author without spaces in ./my_new_role/meta/main.yml
```
sed -i 's/author: your name/author: your_name/' ./meta/main.yml
```
4) testing
```
molecule test
```
5) destroy docker container
```
molecule destroy
```

# Installation with virtualenv:
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
        molecule_install_virtualenv: true
```
Testing:
1) activate virtualenv
```
source molecule/bin/activate
```
2) init test role
```
molecule init role my_new_role --driver-name docker
```
3) go to folder of role
```
cd ./my_new_role
```
3) enter author without spaces in ./my_new_role/meta/main.yml
```
sed -i 's/author: your name/author: your_name/' ./meta/main.yml
```
4) testing
```
molecule test
```
5) destroy docker container
```
molecule destroy
```
6) exit virtualenv
```
deactivate
```

