Sway
=======

[![CICD](https://github.com/jahrik/ansible-sway/actions/workflows/cicd.yml/badge.svg)](https://github.com/jahrik/ansible-sway/actions/workflows/cicd.yml)

Installs and configures Sway

## Suports

* Archlinux
* Ubuntu

Example Playbook
----------------

```yaml
    - hosts: laptops
      roles:
         - { role: jahrik.sway, install: true, sway.terminal: alacritty }
```

License
-------

GPLv2

Author Information
------------------

jahrik@gmail.com

https://homelab.business/
