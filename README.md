# ansible-openvpn
Bootstrap openvpn server. It was tested on Ubuntu 14/16 and CentOS 7. Basic features:

1. Install required packages
2. Create server config
3. Generate server certificates
4. Create client configs and generate client certificates


## Usage

All you need is locate this role in your *roles* directory and use it in your playbooks. 
Also you need to edit *defaults/main.yml* to change default settings if you need it and add clients to the *openvpn_users* list.

Playbook example:
```
---
- hosts: all
  become: true
  roles:
    - { role: 'ansible-openvpn' }
```

**Warning!** If you use Ubuntu 16.04 you need to install python2 first. There is example how to do it via Ansinle:
```
- hosts: all
  become: true
  gather_facts: False

  tasks:
  - name: install python 2
    raw: test -e /usr/bin/python || (apt -y update && apt install -y python-minimal)
```
