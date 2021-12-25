# Ansible role Molecule (for Debian)
Options:
  - Molecule path for root [ /usr/bin ]
  - Molecule path for sudo [ /home/user/.local/bin ]
  - Molecule virtualenv for root [ /root/molecule ]
  - Molecule virtualenv for sudo [ /home/user/molecule ]

System dependencies:
  - Debian
  - Ansible. installed
  - Docker. started

Ansible dependencies:
  - None
# Installation without virtualenv:
1) Install from Github (git installed on your server)
```
ansible-galaxy install darexsu.molecule
```
2) Example playbook
```yaml
---
- hosts: all
  become: yes

  roles:
    - role: ansible-role-molecule
      vars:
        molecule_install: true        
```
Testing:
1) You have to re-login. if you have already logged as molecule-user.
```
exit
```
2) init test role
```
molecule init role my_new_role --driver-name docker
```
3) go to folder of role
```
cd ./my_new_role
```
4) enter author without spaces in ./my_new_role/meta/main.yml
```
sed -i 's/author: your name/author: your_name/' ./meta/main.yml
```
5) testing
```
molecule test
```
6) destroy docker instance
```
molecule destroy
```

# Installation in virtualenv:
1) Install from Github (git installed on your server)
```
ansible-galaxy install darexsu.molecule
```
2) Example playbook
```yaml
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

