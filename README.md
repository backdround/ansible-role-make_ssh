# Ansible role: make_ssh
This role adds ssh config and keys locally for remote nodes. It based
on current connection settings.

It doesn't override current config with another ip / domain_name. If you want
do this, then remove it manually.

### Example playbook
```yml
- hosts: servers
  roles:
    - make_ssh
```
This example make:
```
# Files:
~/.ssh/servers/{{ each_server.hostname }}/id_rsa
~/.ssh/servers/{{ each_server.hostname }}/id_rsa.pub
~/.ssh/servers/{{ each_server.hostname }}/config

# Config content:
Host some_server
  User admin
  HostName some_server.com
  Port 22
  IdentityFile "~/.ssh/servers/some_server/id_rsa"

# And import id_rsa.pub to some_server.com
```
